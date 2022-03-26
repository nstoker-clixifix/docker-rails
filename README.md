# README.md

This repo is based on [Ryan Williams' rails7-on-docker](https://github.com/ryanwi/rails7-on-docker) project.

Applying some personal preferences over time.

## Setup

### Initial Setup

```bash
cp .env.example .env
docker compose build
docker compose run --rm web bin/rails db:setup
```

## Running the Rails app

```bash
docker compose up
```

## Running the Rails console

When the app is already running with docker-compose up, attach to the container:

```bash
docker compose exec web bin/rails c
```

When no container running yet, start up a new one:

```bash
docker compose run --rm web bin/rails c
```

## Running tests

```bash
docker compose run --rm web bin/rspec
```

## Updating gems

```bash
docker compose run --rm web bundle update
docker compose up --build
```

## Credits/References

The original version of this repo [Ryan Williams' rails7-on-docker](https://github.com/ryanwi/rails7-on-docker)

### Rails with Docker

- [Quickstart: Compose and Rails](https://docs.docker.com/compose/rails/)
- [Docker for Rails Developers
Build, Ship, and Run Your Applications Everywhere](https://pragprog.com/book/ridocker/docker-for-rails-developers)
- [Ruby on Whales:
Dockerizing Ruby and Rails development](https://evilmartians.com/chronicles/ruby-on-whales-docker-for-ruby-rails-development)

### Rails 7 with importmaps

- [Alpha preview: Modern JavaScript in Rails 7 without Webpack](https://www.youtube.com/watch?v=PtxZvFnL2i0)

### Rails 7 with hotwire

- [Stimulus 3 + Turbo 7 = Hotwire 1.0](https://world.hey.com/dhh/stimulus-3-turbo-7-hotwire-1-0-9d507133)
- [Turbo 7](https://world.hey.com/hotwired/turbo-7-0dd7a27f)
- [Rails 7 will have three great answers to JavaScript in 2021+](https://world.hey.com/dhh/rails-7-will-have-three-great-answers-to-javascript-in-2021-8d68191b)
- [Hotwire Turbo Replacing Rails UJS](https://www.driftingruby.com/episodes/hotwire-turbo-replacing-rails-ujs)
