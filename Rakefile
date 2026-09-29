# Rakefile with various tasks to make it easier to write with Jekyll

require 'fileutils'
require 'date'
require 'json'
require 'net/http'
require 'open3'
require 'yaml'

namespace :blog do
  desc "Creates a new Jekyll blog post"
  task :create, [:title] do |t, args|
    if args[:title].nil? || args[:title].empty?
      puts "Error: You must provide a title for the post."
      puts "Usage: rake blog:create['Post Title Here']"
      exit
    end

    # Constuct filename & path
    date = Date.today.strftime("%Y-%m-%d")
    # Sanitize the title to create a filename slug, lowercase & sub spaces with hyphens
    filename_slug = args[:title].downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
    filename = "#{date}-#{filename_slug}.md"
    posts_dir = "blog/_posts"
    file_path = File.join(posts_dir, filename)

    content = <<~FRONT_MATTER
      ---
      title: "#{args[:title]}"
      tags:
      ---
    FRONT_MATTER

    File.open(file_path, 'w') do |f|
      f.write(content)
    end

    puts "New blog post created: #{file_path}"
  end
end

namespace :now do
  desc "Updates the last_modified_at date in the now page front matter to today"
  task :update do
    now_page = "_pages/now.md"
    date = Date.today.strftime("%Y-%m-%d")
    content = File.read(now_page)
    updated = content.gsub(/^last_modified_at:.*$/, "last_modified_at: #{date}")
    File.write(now_page, updated)
    puts "Updated #{now_page} last_modified_at to #{date}"
    system("zed #{now_page}")
  end

  desc "Commits changes to the now page and optionally pushes them"
  task :commit do
    now_page = "_pages/now.md"

    diff = `git diff #{now_page}`
    if diff.empty?
      puts "No changes to commit in #{now_page}."
      exit
    end

    puts diff
    print "\nCommit these changes? [y/N] "
    input = $stdin.gets.chomp
    unless input.downcase == 'y'
      puts "Aborted."
      exit
    end

    commit_message = "Update now page - #{`date`.chomp}"
    committed = system("git", "add", now_page) && system("git", "commit", "-m", commit_message)
    abort "Commit failed." unless committed

    upstream = `git rev-parse --abbrev-ref --symbolic-full-name '@{upstream}' 2>/dev/null`.chomp
    abort "Cannot push: the current branch has no upstream branch." if upstream.empty?

    files_to_push = IO.popen(
      ["git", "log", "--format=", "--name-only", "#{upstream}..HEAD"],
      err: File::NULL,
      &:read
    ).lines.map(&:chomp).reject(&:empty?).uniq
    abort "Cannot determine which files will be pushed." unless $?.success?

    puts "\nFiles that will be pushed:"
    files_to_push.each { |file| puts "  #{file}" }
    print "\nPush these changes? [y/N] "
    input = $stdin.gets&.chomp

    if input&.downcase == "y"
      abort "Push failed." unless system("git", "push")
    else
      puts "Committed without pushing."
    end
  end

  desc "Syncs the now page to dakota.omg.lol"
  task :sync do
    api_key = ENV["OMG_KEY"]
    abort "Error: OMG_KEY is not set." if api_key.nil? || api_key.empty?

    now_page = "_pages/now.md"
    source = File.read(now_page)
    page = source.match(/\A---\r?\n(?<front_matter>.*?)^---\s*$\r?\n?(?<body>.*)\z/m)
    abort "Error: Could not parse front matter in #{now_page}." unless page

    metadata = YAML.safe_load(page[:front_matter], permitted_classes: [Date])
    updated_at = Date.parse(metadata.fetch("last_modified_at").to_s)
    body = page[:body]
      .sub(/\{\{\s*page\.last_modified_at\s*\|\s*date:\s*"%A, %B %d, %Y"\s*\}\}/, updated_at.strftime("%A, %B %d, %Y"))
      .sub(/\{\{\s*page\.last_modified_location\s*\}\}/, metadata.fetch("last_modified_location"))
      .sub(/\n---\s*\n\n\*P\.?S\.?\*.*\z/m, "")

    header = <<~MARKDOWN
      {profile-picture}

      # {address}

      {last-updated}

      This page is a mirror of my `/now` page at https://chambers.io/now

      --- Now ---
    MARKDOWN

    footer = <<~MARKDOWN
      ---

      *P.S.* - you can view the [history of this page in GitHub](https://github.com/dcchambers/dcchambers.github.io/commits/master/_pages/now.md) if you're interested.

      (This is a [now page](https://nownownow.com/about). If you have your own site, you should make one too!)

      [Explore the omg.lol now garden.](https://now.garden/)

      [Back to my omg.lol page!](https://{address}.omg.lol)
    MARKDOWN

    content = "#{header.rstrip}\n\n#{body.strip}\n\n#{footer}"

    uri = URI("https://api.omg.lol/address/dakota/now")
    request = Net::HTTP::Post.new(uri)
    request["Authorization"] = "Bearer #{api_key}"
    request["Content-Type"] = "application/json"
    request.body = JSON.generate(content: content)

    http = Net::HTTP.new(uri.host, uri.port)
    http.use_ssl = true
    http.open_timeout = 10
    http.read_timeout = 30
    response = http.request(request)
    payload = JSON.parse(response.body)

    unless response.is_a?(Net::HTTPSuccess) && payload.dig("request", "success")
      message = payload.dig("response", "message") || response.message
      abort "Error syncing now page (HTTP #{response.code}): #{message}"
    end

    puts payload.dig("response", "message")
  rescue JSON::ParserError
    abort "Error syncing now page (HTTP #{response.code}): Invalid JSON response."
  rescue KeyError => e
    abort "Error: Missing #{e.key.inspect} in #{now_page} front matter."
  end
end

namespace :link do
  desc "Creates a new linkblog post"
  task :create, [:title, :link] do |t, args|
    if args[:title].nil? || args[:title].empty?
      puts "Error: You must provide a title for the post."
      puts "Usage: rake link:create['Post Title Here','https://example.com']"
      exit
    end

    # Constuct filename & path
    date = Date.today.strftime("%Y-%m-%d")
    # Sanitize the title to create a filename slug, lowercase & sub spaces with hyphens
    filename_slug = args[:title].downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
    filename = "#{date}-#{filename_slug}.md"
    posts_dir = "linkblog/_posts"
    file_path = File.join(posts_dir, filename)

    content = <<~FRONT_MATTER
      ---
      title: "#{args[:title]}"
      link: "#{args[:link]}"
      via:
      tags:
      ---

      {{ page.link }}
    FRONT_MATTER

    File.open(file_path, 'w') do |f|
      f.write(content)
    end

    puts "New blog post created: #{file_path}"
  end
end

namespace :frontmatter do
  desc "Updates last_modified_at in staged files that have YAML front matter"
  task :update_last_modified_at do
    repository_root, error, status = Open3.capture3("git", "rev-parse", "--show-toplevel")
    abort "Error: Could not find the Git repository root. #{error}" unless status.success?

    Dir.chdir(repository_root.chomp)

    git = lambda do |*args, stdin_data: nil|
      options = { binmode: true }
      options[:stdin_data] = stdin_data unless stdin_data.nil?
      output, error, status = Open3.capture3("git", *args, **options)
      abort "Error: git #{args.join(' ')} failed. #{error}" unless status.success?
      output
    end

    update_frontmatter = lambda do |content, date|
      lines = content.lines
      next unless lines.first&.match?(/\A(?:\xEF\xBB\xBF)?---[ \t]*(?:\r?\n|\z)/n)

      closing_line = (1...lines.length).find do |index|
        lines[index].match?(/\A---[ \t]*(?:\r?\n|\z)/n)
      end
      next unless closing_line

      changed = false
      (1...closing_line).each do |index|
        match = lines[index].match(/\A([ \t]*last_modified_at[ \t]*:[ \t]*)(.*?)([ \t]+#.*)?(\r?\n|\z)\z/n)
        next unless match

        replacement = "#{match[1]}#{date}#{match[3]}#{match[4]}"
        next if replacement == lines[index]

        lines[index] = replacement
        changed = true
      end

      lines.join if changed
    end

    changed_paths = git.call("diff", "--cached", "--name-only", "--diff-filter=ACMRT", "-z").split("\0")
    if changed_paths.empty?
      puts "No staged files to check."
      next
    end

    entries = git.call("ls-files", "--stage", "-z").split("\0").each_with_object({}) do |entry, result|
      metadata, path = entry.split("\t", 2)
      next unless path

      mode, object_id, stage = metadata.split(" ", 3)
      result[path] = { mode: mode, object_id: object_id } if stage == "0"
    end

    date = Date.today.iso8601
    updated_paths = []

    changed_paths.each do |path|
      entry = entries[path]
      next unless entry && %w[100644 100755].include?(entry[:mode])

      staged_content = git.call("cat-file", "blob", entry[:object_id])
      updated_staged_content = update_frontmatter.call(staged_content, date)
      next unless updated_staged_content

      updated_object_id = git.call("hash-object", "-w", "--stdin", stdin_data: updated_staged_content).strip
      index_entry = "#{entry[:mode]} #{updated_object_id} 0\t#{path}\0"
      git.call("update-index", "-z", "--index-info", stdin_data: index_entry)

      unless File.symlink?(path) || !File.file?(path)
        worktree_content = File.binread(path)
        updated_worktree_content = update_frontmatter.call(worktree_content, date)
        File.binwrite(path, updated_worktree_content) if updated_worktree_content
      end

      updated_paths << path
    end

    if updated_paths.empty?
      puts "No staged front matter with a stale last_modified_at date found."
    else
      updated_paths.each { |path| puts "Updated last_modified_at in #{path} to #{date}" }
    end
  end
end
