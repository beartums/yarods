# YARODS
### Yet Another Ruby On Docker Scaffolding
---

Basic outline for a ruby on docker image with associated services -- redis, sidekiq, postgres.  Based on [an excellent blog post](https://evilmartians.com/chronicles/ruby-on-whales-docker-for-ruby-rails-development) by Vladimir Dementyev at Evil Martians.


## Quick Start

  * Fork this repository
  * Clone locally
  * Add .env file, update versions as needed
  * Add to .dockerdev/Aptfile any additional dependencies you want available in the final image
  * `docker-compose build`
  * `docker-compose run --rm --service-ports runner` to get your command prompt
  * install rails (if desired. Overwrite README and .gitignore, if that floats your boat, though you'll want to add the .env file back into the gitignore unless you like pushing your secrets to github repositories)
  * develop

Add to .env file (in root folder) 
```
DATABASE_URL=postgresql://<username>:<password>@postgres:5432
POSTGRES_USER=<username>
POSTGRES_PASSWORD=<password>
```

Terminal prompt: `docker-compose --rm --service-ports runner`

Rails server (once installed): `docker-compose --rm --service-ports rails`

Install rails (from terminal prompt -- see above):
```
gem install rails
git init
git remote remove origin
rails new . --git --database=postgresql
# ADD *url: <%= ENV.fetch('DATABASE_URL') %>* to default profile in config/database.yaml
rails s -b 0.0.0.0
```

Once youve pushed your new app to a repository of your choice, every time you clone it, you'll need to reintall gems and yarn packages, as well as redefine your .env file from the terminal prompt:
```
bundle install
yarn install --check-files
rake db:create
```