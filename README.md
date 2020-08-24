heroku-buildpack-imagemagick
=================================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for vendoring the ImageMagick binaries into your project.

### Install

In your project root:

`heroku buildpacks:add g2/imagemagick --index 1 --app HEROKU_APP_NAME`

"index 1" means that imagemagick will be installed first.

### Changing version
Set the version of ImageMagick you want to install by adding the `IMAGE_MAGICK_VERSION` environment variable to your app:

```bash
heroku config:set IMAGE_MAGICK_VERSION=6.9.10-97 --app HEROKU_APP_NAME
```

The version you wish to install must be available at https://www.imagemagick.org/download/releases. 

Clear cache, as shown below, and redeploy your app to Heroku.

### Clear cache
Since the installation is cached you might want to clean it out due to config changes.

1. `heroku plugins:install heroku-repo`
2. `heroku repo:purge_cache --app HEROKU_APP_NAME`
