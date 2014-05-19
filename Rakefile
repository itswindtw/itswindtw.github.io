require 'date'

deploy_dir = '_deploy'

task :copy_html_files do
  FileList['*.html'].each do |f|
    cp f, deploy_dir
  end
end

task :copy_stylesheets do
  mkdir_p File.join(deploy_dir, 'stylesheets')
  FileList['stylesheets/**/*'].each {|f| cp f, File.join(deploy_dir, File.dirname(f)) }
end

task :clear_prev_deploy do
  FileList["#{deploy_dir}/*"].each { |f| rm_r f }
end

multitask build: %i{copy_html_files copy_stylesheets} do
  puts "All files are ready for deploying"
end

task :deploy => [:clear_prev_deploy, :build] do
  cd deploy_dir do
    system 'git add -A .'
    system "git commit -m \"Site updated at #{DateTime.now}\""
  end
end