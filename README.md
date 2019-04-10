### Phusion Passenger(mod_rails)
---
https://github.com/phusion/passenger

https://www.phusionpassenger.com/library/walkthroughs/start/ruby.html

https://rubygems.org/gems/passenger/versions/5.0.30

```
```

```
git submodule update --init --recursive
git submodule update --init --recursive
./bin/passenger-install-apache2-module
./bin/passenger-install-nginx-module
~/path-to-passenger/bin/passenger start
gem build passenger.gemspec
gem install passenger-x.x.x.gem
```

```sh
git clone https://github.com/phusion/passenger-ruby-rails-demo.git
git clone https://github.com/phusion/passenger-ruby-sinatra-demo.git
cd passenger-ruby-sinatra-demo
cd /path-to-your-app
bundle install
bundle exec passenger start
curl http://0.0.0.0:3000/
bundle exec passenger start
cd /path-to-your-app
bundle exec passenger stop
```

```ruby
gem "passenger", ">= 5.0.25", require: "phusion_passenger/rack_handler"

passenger_rolling_restarts on;
passenger_resist_deployment_errors on;
```
