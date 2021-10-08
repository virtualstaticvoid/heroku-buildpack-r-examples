# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r][buildpack] on Heroku,
to run the package tests using [`tools::testInstalledPackage`][test] for a given list of packages.

## Usage

Execute these commands to get started:

```bash
# get the sources
git clone https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples/package-tests

# initialize git
git init -b main
git add --all
git commit -m "initial"

# create a new heroku application, set the buildpack and deploy
heroku create --stack heroku-20 --buildpack vsv/heroku-buildpack-r

# deploy and inspect the output
git push heroku main

# run R program on Heroku
heroku run R --no-save -f prog.R
```

## License

MIT License. Copyright (c) 2017 Chris Stefano. See [LICENSE](../LICENSE) for details.

<!-- Links -->
[buildpack]: https://github.com/virtualstaticvoid/heroku-buildpack-r
[test]: https://www.rdocumentation.org/packages/tools/versions/3.6.2/topics/testInstalledPackage
