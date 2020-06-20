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
  * install rails (if desired)
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
rails new . --git --database=postgresql
# ADD `url: <%= ENV.fetch('DATABASE_URL') %>` to config/database.yaml
rails s -b 0.0.0.0
```
