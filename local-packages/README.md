# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r][buildpack] on Heroku,
to demonstrate installing R packages from the application directory instead of from CRAN.

This is useful if you use an outdated package, or a private package which is not published on CRAN.

Save the `*.tar.gz` file of the package to the source directory of the application, and use the
`install.packages(...)` method in the `init.R` file to install it.

This example includes the `localpkgs\Rnlminb2_2110.79.tar.gz` file, which is installed using
`install.packages("./localpkgs/Rnlminb2_2110.79.tar.gz", repos=NULL, type="source")`.

**NOTE:** The path to the package file is a _relative_ path so it works on your development
environment and on Heroku.

## Usage

Execute these commands to get started:

```bash
# get the sources
git clone https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples/local-packages

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
