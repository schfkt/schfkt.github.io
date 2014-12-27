# Based on: https://github.com/plusjade/jekyll-bootstrap/blob/master/Rakefile
require 'rake'

POSTS_DIR = File.join('.', '_posts')

# Usage: rake post title="A Title" [date="2012-02-09"] [tags=[tag1,tag2]] [category="category"]
desc "Begin a new post in #{POSTS_DIR}"
task :post do
  title = ENV["title"] || "new-post"
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  begin
    date = (ENV['date'] ? Time.parse(ENV['date']) : Time.now).strftime('%Y-%m-%d')
  rescue => e
    puts "Error - date format must be YYYY-MM-DD, please check you typed it correctly!"
    exit -1
  end
  filename = File.join(POSTS_DIR, "#{date}-#{slug}.md")
  if File.exist?(filename) && ask("#{filename} already exists. Overwrite?", ['y', 'n']) == 'n'
    abort("rake aborted!")
  end

  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts "date: #{date}"
    post.puts "---"
  end
end

desc 'Run jekyll server -w'
task :s do
  system 'jekyll serve -w'
end