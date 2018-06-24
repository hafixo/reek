require 'bundler/gem_tasks'
require 'rake/clean'

Dir['tasks/**/*.rake'].each { |t| load t }

task :ci do
  [
    'test:spec',
    'configuration:update_default_configuration',
    'test:features',
    :rubocop,
    'test:quality',
    :ataru
  ].each do |name|
    puts "\n=== Running #{name}...\n"
    Rake::Task[name].invoke
    puts "\n=== Running #{name} -> Done\n"
  end
end

task default: :ci
