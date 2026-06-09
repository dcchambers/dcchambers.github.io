# Rakefile with various tasks to make it easier to write with Jekyll

require 'fileutils'
require 'date'

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
