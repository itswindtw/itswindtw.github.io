# A sample Guardfile
# More info at https://github.com/guard/guard#readme

guard 'sass', :input => 'sass', :output => 'stylesheets'

guard 'slim', :slim_options => { :pretty => true } do
  watch(%r{^.+\.slim$})
end

guard 'livereload', grace_period: 0.5 do
  watch(%r{^.+\.html$})
  watch(%r{stylesheets/.+\.css$})
end
