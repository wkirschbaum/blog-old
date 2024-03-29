---
layout: post
title: Starting a Rails Project
date: 2019-03-17T09:01:49+02:00
categories: rails programming
---

This is the minimum setup I feel comfortable when starting a new rails project.

### Links to the gems used in this post

- [rails](https://github.com/rails/rails) Ruby on Rails
- [annotate_models](https://github.com/ctran/annotate_models) Generates schema data as comments in your code files
- [rspec-rails](https://github.com/rspec/rspec-rails) A great testing library with many powerful features
- [factory_bot_rails](https://github.com/thoughtbot/factory_bot_rails) Generates useful factories for testing
- [pry](https://github.com/pry/pry) A powerful irb alternative
- [rubocop](https://github.com/rubocop-hq/rubocop) The ruby style guide as a gem
- [rubocop-rspec](https://github.com/rubocop-hq/rubocop-rspec) Rspec extensions for rubocop
- [pry-doc](https://github.com/pry/pry-doc) Documentation in the Pry REPL

### Generate the necessary Rails files

```bash
$ rails new awesomeproject -T --database=postgresql --skip-coffee
```

### Gems to add to help us to write code

We removed Rails testing with the `-T` flag before, so that we can add `rspec`.

```ruby
group :development, :test do
    ...
    gem 'rspec-rails'
    gem 'factory_bot_rails'
end
```

then run

```bash
$ bundle install
```

```bash
$ rails generate rspec:install
```

### Some nice debugging tools

```ruby
group :development, :test do
    ...
    gem 'pry'
    gem 'pry-doc'
end

group :development do
    ...
    gem 'annotate'
end
```

then run

```bash
$ bundle install
```

```bash
$ rails g annotate:install
```

### For some styling confidence

```ruby
group :development do
    ...
    gem 'rubocop'
    gem 'rubocop-rspec'
end
```

then run

```bash
$ bundle install
```

and add a file `.rubocop.yml` in your project root folder

```yaml
require: rubocop-rspec
```

### Tweak the generators

Add this to your `config/application.rb` file to prevent unnecessary files to be generated automatically, unless you need them.

```ruby
config.generators do |g|
    g.helper false
    g.assets false
    g.skip_routes true
end
```

### Starting with a clean slate

run

```bash
$ rubocop -aR
```

and commit your changes to start development on your awesome project


### Full initial Gemfile

```ruby
# frozen_string_literal: true

source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '2.6.2'

gem 'jbuilder', '~> 2.5'
gem 'pg', '>= 0.18', '< 2.0'
gem 'puma', '~> 3.11'
gem 'rails', '~> 6.0.0.beta3'
gem 'sass-rails', '~> 5.0'
gem 'turbolinks', '~> 5'
gem 'webpacker', '>= 4.0.0.rc.3'

gem 'bootsnap', '>= 1.4.1', require: false

group :development, :test do
  gem 'byebug'
  gem 'factory_bot_rails'
  gem 'rspec-rails', '~> 3.8'
end

group :development do
  gem 'listen', '>= 3.0.5', '< 3.2'
  gem 'web-console', '>= 3.3.0'

  gem 'spring'
  gem 'spring-watcher-listen', '~> 2.0.0'

  gem 'annotate'
  gem 'rubocop'
  gem 'rubocop-rspec'
end
```
