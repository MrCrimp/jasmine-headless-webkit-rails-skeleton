This is a skeleton app demonstrating [jasmine-headless-webkit](http://johnbintz.github.com/jasmine-headless-webkit/). Be sure to check that page for detailed instructions.

Check this out if you want to:

* write Jasmine specs
* use CoffeeScript
* leverage the assets pipeline in Rails 3.1
* run specs headless & quickly enough to remove browser-refreshing from your workflow


##Prerequisites

Stuff I did on my Mac OS X Lion (10.7) setup to get started. I already had XCode installed, which I'll bet is a requisite step.

Install XCode

Install QT with [homebrew](https://github.com/mxcl/homebrew). (Full disclosure: upon running `brew update`, I needed to `/usr/local` and `git stash` and `git pull` to get the latest recipes.)

    brew update
    brew install qt

Install [Growl](http://growl.info/index.php) for guard notifications.

##Try it out

Once you've cloned this repository and changed into the directory, you can run the specs like so:

    bundle install
    bundle exec jasmine-headless-webkit -c --keep

If you run guard, it'll run any specs and it'll monitor any changes to your assets or specs and notify the terminal & growl.

    bundle exec guard


##Replay

If you're looking to recreate a similar setup for your existing project, here are the steps I took.

Added to your Gemfile:

    group :test, :development do
      gem 'jasmine'
      gem 'jasmine-headless-webkit'
  
      if RUBY_PLATFORM =~ /darwin/i
        gem 'growl_notify'
        gem 'rb-fsevent', :require => false 
      end
      gem 'guard-rails-assets'
      gem 'guard-jasmine-headless-webkit'
    end
    
Next, Run:

    jasmine init

This will create a little structure, most importantly your `spec/javascripts/support/jasmine.yml` configuration file. You can safely remove `lib/tasks/jasmine.rake`, though.

Then, update your jasmine.yml file to look for CoffeeScript in the assets directories. Mine looks something like this.

    src_files:
      - "vendor/**/*.{js,coffee}"
      - "lib/**/*.{js,coffee}"
      - "public/**/*.{js,coffee}"
    helpers:
      - "helpers/**/*.{js,coffee}"
    spec_files:
      - "**/*[Ss]pec.{js,coffee}"
    src_dir:
    spec_dir: spec/javascripts

