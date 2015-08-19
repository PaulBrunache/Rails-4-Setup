```ruby

bin/rails generate minitest:install
```

Set up the rails generators to use minitest and fabrication

```ruby
# config/application.rb
# Use Minitest for testing. Fabrication instead of fixtures.
config.generators do |g|
  g.test_framework      :minitest, spec: true, fixture_replacement: :fabrication
  g.fixture_replacement :fabrication, dir: "test/fabricators"
end
```
Generate the sample Guardfile

```
bundle exec guard init minitest
```


Enable the Rails 4 settings. Note: Using MiniTest::Spec but the test file names are the MiniTest::Unit names. ex: test/mymodel_test.rb.

Don't run all tests automatically when guard starts. This can take a while.

```
# Guardfile
guard(:minitest, all_on_start: false,
      all_after_pass: false,
      notification: true) do
  # with Minitest::Unit
  # watch(%r{^test/(.*)\/?test_(.*)\.rb$})
  # watch(%r{^lib/(.*/)?([^/]+)\.rb$})     { |m| "test/#{m[1]}test_#{m[2]}.rb" }
  # watch(%r{^test/test_helper\.rb$})      { 'test' }

  # with Minitest::Spec
  # watch(%r{^spec/(.*)_spec\.rb$})
  # watch(%r{^lib/(.+)\.rb$})         { |m| "spec/#{m[1]}_spec.rb" }
  # watch(%r{^spec/spec_helper\.rb$}) { 'spec' }

  # Rails 4
  watch(%r{^app/(.+)\.rb$})                               { |m| "test/#{m[1]}_test.rb" }
  watch(%r{^app/controllers/application_controller\.rb$}) { 'test/controllers' }
  watch(%r{^app/controllers/(.+)_controller\.rb$})        { |m| "test/integration/#{m[1]}_test.rb" }
  watch(%r{^app/views/(.+)_mailer/.+})                   { |m| "test/mailers/#{m[1]}_mailer_test.rb" }
  watch(%r{^lib/(.+)\.rb$})                               { |m| "test/lib/#{m[1]}_test.rb" }
  watch(%r{^test/.+_test\.rb$})
  # watch(%r{^test/test_helper\.rb$}) { 'test' }

end

```
