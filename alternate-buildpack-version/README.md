# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r](https://github.com/virtualstaticvoid/heroku-buildpack-r) on Heroku,
to demonstrate using a different version of the buildpack.

This is done by setting the `BUILD_PACK_VERSION` environment variable to the desired version.

The list of buildpack versions is published on the [heroku-buildpack-r](https://github.com/virtualstaticvoid/heroku-buildpack-r) repository.

```bash
# get the head revision of this source
git clone --depth=1 https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples

# remove git since we'll reinitialize in the example directory
rm -rf .git

# change to this example's directory
cd alternate-buildpack-version

# initialize git and commit
git init
git add --all
git commit -m "initial"

# create a new heroku application and deploye
heroku create --buildpack https://github.com/virtualstaticvoid/heroku-buildpack-r.git#heroku-16

# set the version(s) to use
heroku config:set BUILD_PACK_VERSION="20180110-2010"

# deploy the application
git push heroku master

# check the logs
heroku logs

# test it out
heroku run R --no-save -f /app/prog.R
```
