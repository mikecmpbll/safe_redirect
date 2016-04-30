# SafeRedirect

A little gem to keep our Rails app safe from open redirection vulnerabilities.

## Installation

Add this line to Gemfile.

```
gem 'safe_redirect'
```

##  Usage

Create a `config/initializer/safe_redirect.rb` file.

```rb
SafeRedirect.configure do |config|
  config.domain_whitelists = ['www.google.com']
  config.default_path = 'https://www.yahoo.com'
end
```

Add this line to the controllers you wish to secure from open redirection.

```rb
include SafeRedirect
```

The `redirect_to` method provided by Rails will be overrode by `safe_redirect`'s `redirect_to` method.

```rb
redirect_to 'https://www.google.com' # => redirects to https://www.google.com
redirect_to 'https://www.golgege.com' # => redirects to ''
redirect_to 'https://www.golgege.com/hahaha' # => redirects to '/hahaha'
redirect_to 1234 # => redirects to https://www.yahoo.com as default path
```

## Contributing

- Fork the repository
- Create a branch for a new feature, build it
- Create a pull request

## License

MIT License

## Author

- [Edwin Tunggawan](https://github.com/sdsdkkk)