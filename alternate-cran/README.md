# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r][buildpack] on Heroku,
to demonstrate using a different CRAN mirror to use when installing R packages.

This is done by setting the `CRAN_MIRROR` environment variable to the desired CRAN mirror's URL.

## Usage

Execute these commands to get started:

```bash
# get the sources
git clone https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples/alternate-cran

# initialize git
git init -b main
git add --all
git commit -m "initial"

# create a new heroku application, set the buildpack and deploy
heroku create --stack heroku-20 --buildpack vsv/heroku-buildpack-r

# set the CRAN URL to use
heroku config:set CRAN_MIRROR="http://cloud.r-project.org"

# deploy
git push heroku main
```

## License

MIT License. Copyright (c) 2017 Chris Stefano. See [LICENSE](../LICENSE) for details.

<!-- Links -->
[buildpack]: https://github.com/virtualstaticvoid/heroku-buildpack-r
