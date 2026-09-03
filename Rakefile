# Rakefile with various tasks to make it easier to write with Jekyll

require 'fileutils'
require 'date'
require 'json'
require 'net/http'
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

  desc "Commits changes to the now page after showing a diff and asking for confirmation"
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
    system("git add #{now_page} && git commit -m '#{commit_message}'")
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
