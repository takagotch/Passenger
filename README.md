### Phusion Passenger(mod_rails)
---
https://github.com/phusion/passenger

https://www.phusionpassenger.com/library/walkthroughs/start/ruby.html

https://rubygems.org/gems/passenger/versions/5.0.30

```
// doc/.md
void foo(const shared_ptr<Client> &client) {
  performNetworking();
  log(client->getAddress());
}

static shared_ptr<Client> client;

void performNetworking() {
  if (write(...) == -1) {
    client.reset();
  }
}

void foo(const shared_ptr<Client> &client) {
  shared_ptr<Client> extraReference = client;
  performNetworking();
  log(client->getAddress());
}

void callback(ev::io &io, int revents) {
  shared_ptr<Foo> extraReference = shared_from_this();
}

worker_processes 2;

http {
  error_log /home/nginx/error.log;
}


program_name1=error1:probability1,error2:probability2,..;program_name2=...

[locations]
natively_packaged=true
bin_dir=/usr/bin
support_binaries_dir=/usr/lib/phusion-passenger/support-binaries
lib_dir=/usr/lib/phusion-passenger
helper_scripts_dir=/usr/share/phusion-passenger/helper-scripts
resources_dir=/usr/share/phusion-passenger
include_dir=/usr/share/phusion-passenger
doc_dir=/usr/share/doc/phusion-passenger
ruby-libdir=/user/lib/ruby/vendor_ruby
apache2_module_path=/usr/lib/apache2/modules/mod_passenger.so
ruby_extension_source_dir=/usr/share/phusion=passenger/ruby_extension_source
nginx_module_source_dir=/usr/share/phusion-passenger/ngx_http_passenger_module
```

```
rake package:gem
rake package:tarball

rake test:cxx
rake test:integration:apache2
rake test:integration:nginx

./start

cd /home/vagrant/nginx
rake boostrap

cd /vagarnt
rake apache2
sudo a2enmod passenger
sudo service apache2 restart

export PASSENGER_SIMULATE_SYSCALL_FAILURES='PassengerAgent watchdog=ENOSPC:0.01;PassengerAgent core=EMFILE:0.001,ECONNREFUSED:0.02'

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
