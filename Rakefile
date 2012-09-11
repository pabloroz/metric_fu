$LOAD_PATH << '.'
require 'rake'
require 'rake/rdoctask'
require 'rspec/core/rake_task'
#require 'rspec/core/rake'
require 'lib/metric_fu'

desc "Run all specs in spec directory"
RSpec::Core::RakeTask.new(:spec) do |t|
  t.pattern = FileList['spec/**/*_spec.rb']
end

MetricFu::Configuration.run do |config|
  config.roodi    = config.roodi.merge(:roodi_config => 'config/roodi_config.yml')
  config.churn    = { :start_date => "1 year ago", :minimum_churn_count => 10}
  config.hotspots = { :start_date => "1 year ago", :minimum_churn_count => 10}
end

task :default => :spec
