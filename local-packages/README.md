# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r](https://github.com/virtualstaticvoid/heroku-buildpack-r) on Heroku,
to demonstrate installing R packages from the application directory instead of from CRAN.

This is desirable if you use an outdated package, or have a private package which is not published on CRAN.

Place the `tar.gz` file of the package into the root or a sub-directory of the application, and add a line of code to the `init.R` file to install it from that directory.

This example includes the `localpkgs\Rnlminb2_2110.79.tar.gz` file, and it is installed using `install.packages("/app/localpkgs/Rnlminb2_2110.79.tar.gz", repos=NULL, type="source")`.

Notice that the path to the package file is fully qualified, and is rooted in `/app` since this is default location for the application files when deployed on Heroku.

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
heroku create --buildpack https://github.com/virtualstaticvoid/heroku-buildpack-r.git

# deploy the application
git push heroku master

# check the logs
heroku logs

# test it out
heroku run R --no-save -f /app/prog.R
```
