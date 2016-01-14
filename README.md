[github]: https://github.com/neopoly/facebook_canvas
[doc]: http://rubydoc.info/github/neopoly/facebook_canvas/master/file/README.md
[gem]: https://rubygems.org/gems/facebook_canvas
[travis]: https://travis-ci.org/neopoly/facebook_canvas
[codeclimate]: https://codeclimate.com/github/neopoly/facebook_canvas
[inchpages]: https://inch-ci.org/github/neopoly/facebook_canvas

# FacebookCanvas

[![Travis](https://img.shields.io/travis/neopoly/facebook_canvas.svg?branch=master)][travis]
[![Gem Version](https://img.shields.io/gem/v/facebook_canvas.svg)][gem]
[![Code Climate](https://img.shields.io/codeclimate/github/neopoly/facebook_canvas.svg)][codeclimate]
[![Test Coverage](https://codeclimate.com/github/neopoly/facebook_canvas/badges/coverage.svg)][codeclimate]
[![Inline docs](https://inch-ci.org/github/neopoly/facebook_canvas.svg?branch=master&style=flat)][inchpages]

Make your Rails application fit to run in a Facebook canvas.


## Why?

Web apps need to handle both `GET` and `POST` requests, but in Facebook canvas apps all requests coming from Facebook are `POST` requests. `FacebookCanvas` provides a way to differentiate between `GET` and `POST` anyway.


## Installation

Add this line to your application's Gemfile:

```ruby
gem 'facebook_canvas'
```


## Configuration

`FacebookCanvas.server_name` is a regular expression that matches the url to your Facebook *Secure Canvas URL*.

The default value is set to: `/\.fb\./`

This means if your *Secure Canvas URL* is available through:

`https://<something>.fb.<something>.<something>/` e.g. `https://my-project.fb.neopoly.com/` it works out of the box without any additional configuration.

If your *Secure Canvas URL* differs from this pattern you can reconfigure the default `FacebookCanvas.server_name` inside an initializer.

```ruby
# config/initializers/facebook_canvas.rb

FacebookCanvas.server_name = /SERVERNAME/
```


## How does this work?

First check whether the request was originally a `GET` request.
For that we assume that Rails inserts a hidden parameter with UTF8 for all non `GET` requests.
So if this parameter is missing, the request is a `GET` request and therefor the `REQUEST_METHOD` is set to `GET`.

The second action which this enigne does, is to save the `SIGNED_REQUEST` in the `default_url_options` hash.
So you have access about the user over the entire application.


## Ruby support

This gem supports Ruby version 2.1 and 2.2.


## Contributing

1. [Fork it!](http://github.com/neopoly/facebook_canvas/fork)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request


## License

FacebookCanvas is released under the MIT License. See the MIT-LICENSE file for further
details.
