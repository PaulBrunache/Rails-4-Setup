# default-gem-list
```ruby 
source 'https://rubygems.org'
ruby '2.2.1'

gem 'rails', '4.2.3'
gem 'sass-rails', '~> 5.0'
gem 'uglifier', '>= 1.3.0'
gem 'coffee-rails', '~> 4.1.0'
gem 'jquery-rails', '~> 4.0.4'
gem 'turbolinks', '~> 2.5.3'
gem 'jbuilder', '~> 2.3.1'
gem 'sdoc', '~> 0.4.0', group: :doc
gem 'bcrypt', '~> 3.1.10'
gem "slim-rails"

group :development do
  gem 'pry'
end
group :test do
  gem 'minitest-rails-capybara'
  gem 'minitest-reporters'
end
group :development, :test do
  gem 'sqlite3'
  gem 'fabrication'
  gem 'guard' 
  gem 'guard-minitest'
end


group :production do
  gem 'pg',             '0.17.1'
  gem 'rails_12factor', '0.0.2'
  gem 'puma',           '2.11.1'
end
```
