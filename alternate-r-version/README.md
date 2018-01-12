# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r](https://github.com/virtualstaticvoid/heroku-buildpack-r) on Heroku,
to demonstrate using a different version of R.

This is done by setting the `R_VERSION` environment variable to the desired version.

```bash
# get the head revision of this source
git clone --depth=1 https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples

# remove git since we'll reinitialize in the example directory
rm -rf .git

# change to this example's directory
cd alternate-r-version

# initialize git and commit
git init
git add --all
git commit -m "initial"

# create a new heroku application and deploye
heroku create --buildpack https://github.com/virtualstaticvoid/heroku-buildpack-r.git#heroku-16

# set the version(s) to use
heroku config:set R_VERSION="3.4.0"

# deploy the application
git push heroku master

# check the logs
heroku logs

# test it out
heroku run R --no-save -f /app/prog.R
```
