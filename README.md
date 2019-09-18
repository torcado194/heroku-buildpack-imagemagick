heroku-buildpack-imagemagick
=================================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring the ImageMagick binaries into your project.

This one works with [Heroku stack](https://devcenter.heroku.com/articles/stack) `heroku-18`.

### Install

In your project root:

`heroku buildpacks:add https://github.com/q-m/heroku-buildpack-imagemagick  --index 1 --app HEROKU_APP_NAME`

"index 1" means that imagemagick will be installed first.

### Changing version
Go to https://www.imagemagick.org/download/releases and find a version you want (*.tar.gz).
You can set the environment variable `IMAGE_MAGICK_VERSION` to the desired version (e.g. `6.9.10-59`).
Clear cache, as shown below, and redeploy your app to Heroku.

By default, the `bin/compile` script will look for the latest 6.x version from the releases page.

### Clear cache
Since the installation is cached you might want to clean it out due to config changes.

1. `heroku plugins:install heroku-repo`
2. `heroku repo:purge_cache -app HEROKU_APP_NAME`
