# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r][buildpack] on Heroku,
to demonstrate the use of environment variables from R during slug compilation and at runtime.

This example sets the `MYVAR1` and `MYVAR2` environment variables. Check the deploy log, or
console output to see their values displayed.

## Usage

Execute these commands to get started:

```bash
# get the sources
git clone https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples/environment

# initialize git
git init -b main
git add --all
git commit -m "initial"

# create a new heroku application, set the buildpack and deploy
heroku create --stack heroku-20 --buildpack vsv/heroku-buildpack-r

# set values for MYVAR1 and MYVAR2
heroku config:set MYVAR1="foo" MYVAR2="bar"

# deploy and inspect the output
git push heroku main

# inspect the log output
heroku logs

# run R program on Heroku
heroku run R --no-save -f prog.R
```

## License

MIT License. Copyright (c) 2017 Chris Stefano. See [LICENSE](../LICENSE) for details.

<!-- Links -->
[buildpack]: https://github.com/virtualstaticvoid/heroku-buildpack-r
