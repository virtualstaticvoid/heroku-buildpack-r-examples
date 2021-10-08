# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r][buildpack] on Heroku,
to demonstrate use of the [RPostgreSQL][package] package.

## Usage

Execute these commands to get started:

```bash
# get the sources
git clone https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples/postgresql

# initialize git
git init -b main
git add --all
git commit -m "initial"

# create a new heroku application, set the buildpack and deploy
heroku create --stack heroku-20 --buildpack vsv/heroku-buildpack-r

# create postgres database (free)
heroku addons:create heroku-postgresql:hobby-dev

# deploy and inspect the output
git push heroku main

# run R program on Heroku
heroku run R --no-save -f prog.R
```

## License

MIT License. Copyright (c) 2017 Chris Stefano. See [LICENSE](../LICENSE) for details.

<!-- Links -->
[buildpack]: https://github.com/virtualstaticvoid/heroku-buildpack-r
[package]: https://cran.r-project.org/web/packages/RPostgreSQL/index.html
