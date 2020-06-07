# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r](https://github.com/virtualstaticvoid/heroku-buildpack-r) on Heroku,
to demonstrate using a different CRAN mirror to use when installing R packages.

This is done by setting the `CRAN_MIRROR` environment variable to the desired CRAN mirror's URL.

```bash
# get the head revision of this source
git clone --depth=1 https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples

# remove git since we'll reinitialize in the example directory
rm -rf .git

# change to this example's directory
cd alternate-cran

# initialize git and commit
git init
git add --all
git commit -m "initial"

# create a new heroku application and deploye
heroku create --buildpack https://github.com/virtualstaticvoid/heroku-buildpack-r.git

# set the CRAN URL to use
heroku config:set CRAN_MIRROR="http://cloud.r-project.org"

# deploy the application
git push heroku master

# check the logs
heroku logs

# test it out
heroku run R --no-save -f /app/prog.R
```
