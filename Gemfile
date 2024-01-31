source "https://rubygems.org"

# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#

# If you have any plugins, put them here!

gem "bundler"
gem "jekyll"

group :jekyll_plugins do
    gem "jekyll-paginate"
    gem "jekyll-sitemap"
    gem "jekyll-include-cache"
    gem "jekyll-target-blank"
end

group :test do
    gem "html-proofer", "~> 4.4"
end

# TODEL condition; it was added as a workaround for https://github.com/actions/jekyll-build-pages/issues/104
gem 'faraday-retry', '~> 2.2.0' if ENV["GITHUB_ACTIONS"] != "true"