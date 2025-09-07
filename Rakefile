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
