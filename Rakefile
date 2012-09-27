# -*- encoding: utf-8 -*-

task :default => :build

desc 'Configure and build kupfer'
task :build do
  sh *%W[./waf configure --prefix=#{ENV['PREFIX'] || '/opt/kupfer'}]
end

desc 'Install kupfer'
task :install do
  sh './waf install'
end
