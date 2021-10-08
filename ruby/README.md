# Example R App on Heroku

This is an example R application, which uses the [heroku-buildpack-r][buildpack] on Heroku,
to demonstrate using Ruby, with Sinatra API and the [rinruby][rinruby] gem.

![Screenshot][screenshot.png]

## Usage

Execute these commands to get started:

```bash
# get the sources
git clone https://github.com/virtualstaticvoid/heroku-buildpack-r-examples.git
cd heroku-buildpack-r-examples/rmarkdown

# initialize git
git init -b main
git add --all
git commit -m "initial"

# create a new heroku application, set the buildpack and deploy
heroku create --stack heroku-20 --buildpack vsv/heroku-buildpack-r

# add the ruby buildpack
heroku buildpacks:add heroku/ruby

# deploy and inspect the output
git push heroku main

# view the application
heroku open
```

## License

MIT License. Copyright (c) 2017 Chris Stefano. See [LICENSE](../LICENSE) for details.

<!-- Links -->
[buildpack]: https://github.com/virtualstaticvoid/heroku-buildpack-r
[rinruby]: https://rubygems.org/gems/rinruby
