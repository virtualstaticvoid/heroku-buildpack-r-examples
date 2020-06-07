# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r](https://github.com/virtualstaticvoid/heroku-buildpack-r) on Heroku,
to demonstrate the use of environment variables from R during slug compilation and at runtime.

This example sets the `MYVAR1` and `MYVAR2` environment variables. Check the deploy log, or console output to see their values displayed.

```bash
# get the head revision of this source
git clone --depth=1 https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples

# remove git since we'll reinitialize in the example directory
rm -rf .git

# change to this example's directory
cd environment

# initialize git and commit
git init
git add --all
git commit -m "initial"

# create a new heroku application and deploye
heroku create --buildpack https://github.com/virtualstaticvoid/heroku-buildpack-r.git

# set values for MYVAR1 and MYVAR2
heroku config:set MYVAR1="foo" MYVAR2="bar"

# deploy the application
git push heroku master

# check the logs
heroku logs

# test it out
heroku run R --no-save -f /app/prog.R
```
