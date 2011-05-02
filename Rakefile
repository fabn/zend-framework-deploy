# encoding: utf-8

require 'rubygems'
require 'bundler'
begin
  Bundler.setup(:default, :development)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end
require 'rake'

require 'jeweler'
Jeweler::Tasks.new do |gem|
  # gem is a Gem::Specification... see http://docs.rubygems.org/read/chapter/20 for more options
  gem.name = "zend-framework-deploy"
  gem.homepage = "http://github.com/fabn/zend-framework-deploy"
  gem.license = "MIT"
  gem.summary = %Q{Deploy Zend Framework applications with Capistrano}
  gem.description = %Q{Use this gem to deploy Zend Framework projects with Capistrano. It will adapt Capistrano configuration in order to be used with ZF project structure.}
  gem.email = "f.napoleoni@gmail.com"
  gem.authors = ["Fabio Napoleoni"]
  # dependencies defined in Gemfile
end
Jeweler::RubygemsDotOrgTasks.new
