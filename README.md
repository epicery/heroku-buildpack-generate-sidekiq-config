# Heroku Buildpack: GenerateSidekiqConfig

## Description
This buildpack configures Sidekiq using a file named `./.heroku/sidekiq.yml`. It also searches for a rake task named `"heroku:generate-sidekiq-config"` and executes it if it exists.

You would typically create such a rake task if your app is deployed on different platforms. For instance, at _epicery_ we use heroku to host our pre-production application for which we don't want/need to split our Sidekiq queues among several dynos. We therefore implement a task that concatenates all our production configuration files in a single one just for heroku.

## Usage
```
# provided the current directory is your project's root directory:
heroku buildpacks:add https://github.com/epicery/heroku-buildpack-generate-sidekiq-config
git push heroku master
```
