# RemoteFactoryGirlHomeRails

Create [FactoryGirl](https://github.com/thoughtbot/factory_girl) factories
remotely using [RemoteFactoryGirl](https://github.com/tdouce/remote_factory_girl). 

Integration testing SOA (Software Oriented Architecture) apps is an inherently 
difficult problem (Rails apps included :). SOA is comprised of multiple applications, 
and while individual apps can be tested (and presumably passing) in isolation (usually by 
mocking http requests), it does not guarantee the apps will work in unison. Testing 
interactions between apps is more difficult. 

One problem with integration testing SOA apps is that it is difficult to write 
integration tests in the client. Due to the nature of SOA you can not 
create the data you need when you need it because the database you need to create the data
resides in another application.  It is possible to create test data in traditional apps (apps 
that contain a database) with tools such as [FactoryGirl](https://github.com/thoughtbot/factory_girl). 
However, in SOA apps FactoryGirl alone does not suffice. RemoteFactoryGirlHome
when used in conjunction with [RemoteFactoryGirl](https://github.com/tdouce/remote_factory_girl),
builds on top of [FactoryGirl](https://github.com/thoughtbot/factory_girl) (because
we all work on the backs of giants) and provides a mechanism to create the data you need 
when you need it in the *home* app from a client app.

## Installation

Add this line to your application's Gemfile:

```ruby
group :test do
  gem 'remote_factory_girl_home'
end
```


And then execute:

    $ bundle


## Usage

Configure in `config/routes.rb`

```ruby
YourApplication::Application.routes.draw do
  if defined?(RemoteFactoryGirlHomeRails::Engine)
    mount RemoteFactoryGirlHomeRails::Engine, at: '/remote_factory_girl' 
  end
end
```

## Run tests


    $ rspec


## Contributing

1. Fork it ( http://github.com/<my-github-username>/remote_factory_girl_home/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
