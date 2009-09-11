$:.unshift 'lib'
require 'rubygems'
require 'rake'
require 'rake/testtask'
require 'rake/rdoctask'
require 'spec/rake/spectask'

HANOI_VERSION = "0.0.1.1"

task :default => :spec

desc 'Build and install the gem (useful for development purposes).'
task :install do
  system "gem build hanoi++.gemspec"
  system "sudo gem uninstall hanoi++"
  system "sudo gem install --local --no-rdoc --no-ri hanoi++-#{HANOI_VERSION}.gem"
  system "rm hanoi++-*.gem"
end

Spec::Rake::SpecTask.new do |t|
  t.spec_files = FileList['spec/**/*_spec.rb']
  t.spec_opts = %w(-fs --color)
end

desc 'Show the file list for the gemspec file'
task :files do
  puts "Files:\n #{Dir['**/*'].reject {|f| File.directory?(f)}.sort.inspect}"
  puts "Test files:\n #{Dir['spec/**/*_spec.rb'].reject {|f| File.directory?(f)}.sort.inspect}"
end
