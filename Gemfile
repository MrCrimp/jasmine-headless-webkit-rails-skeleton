source 'http://rubygems.org'

gem 'rails', '~> 3.1.0.rc'

# Bundle edge Rails instead:
# gem 'rails',     :git => 'git://github.com/rails/rails.git'

gem 'sqlite3'

gem 'json'

# Gems used only for assets and not required
# in production environments by default.
group :assets do
  gem 'sass-rails', "  ~> 3.1.0.rc"
  gem 'coffee-rails', "~> 3.1.0.rc"
  gem 'uglifier'
end

gem 'jquery-rails'

group :test, :development do
  gem 'jasmine'
  gem 'jasmine-headless-webkit'
  gem 'guard-rails-assets'
  gem 'guard-jasmine-headless-webkit'
  if RUBY_PLATFORM =~ /darwin/i
    gem 'growl_notify'
    gem 'rb-fsevent', :require => false
  end
end

# Use unicorn as the web server
# gem 'unicorn'

# Deploy with Capistrano
# gem 'capistrano'

# To use debugger
# gem 'ruby-debug'
