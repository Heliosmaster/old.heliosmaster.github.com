require 'rake'
require 'yaml'

SOURCE = "."
CONFIG = {
  'posts' => File.join(SOURCE, "_posts"),
  'post_ext' => "md",
}

# Usage: rake post title="A Title" date="2012-02-09"
desc "Begin a new post in #{CONFIG['posts']}"
task :post do
  abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
  title = ENV["title"] || "new-post"
  slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
  begin
    date = Time.now.strftime('%Y-%m-%d')
  rescue Exception => e
    puts "Error - date format must be YYYY-MM-DD, please check you typed it correctly!"
    exit -1
  end
  filename = File.join(CONFIG['posts'], "#{date}-#{slug}.#{CONFIG['post_ext']}")
  if File.exist?(filename)
    abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
  end
  
  puts "Creating new post: #{filename}"
  open(filename, 'w') do |post|
    post.puts "---"
    post.puts "layout: post"
    post.puts "title: \"#{title.gsub(/-/,' ')}\""
    post.puts "tags: "
    post.puts "---"
  end
end # task :post

# # Usage: rake post title="A Title"
# desc "Begin a new post in #{CONFIG['posts']}"
# task :post do
#   abort("rake aborted: '#{CONFIG['posts']}' directory not found.") unless FileTest.directory?(CONFIG['posts'])
#   title = ENV["title"] || "new-post""
#   slug = title.downcase.strip.gsub(' ', '-').gsub(/[^\w-]/, '')
#   filename = File.join(CONFIG['posts'], #{Time.now.strftime('%Y-%m-%d')}-#{slug}.#{CONFIG['post_ext']}")
#   if File.exist?(filename)
#     abort("rake aborted!") if ask("#{filename} already exists. Do you want to overwrite?", ['y', 'n']) == 'n'
#   end
  
#   puts "Creating new post: #{filename}"
#   open(filename, 'w') do |post|
#     post.puts "---"
#     post.puts "layout: post"
#     post.puts "title: \"#{title.gsub(/-/,' ')}\""
#     post.puts "tags: "
#     post.puts "---"
#   end
# end # task :post