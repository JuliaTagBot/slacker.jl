# Slacker

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://sumidu.github.io/Slacker.jl/stable)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://sumidu.github.io/Slacker.jl/dev)
[![Build Status](https://travis-ci.com/sumidu/Slacker.jl.svg?branch=master)](https://travis-ci.com/sumidu/Slacker.jl)
[![Build Status](https://ci.appveyor.com/api/projects/status/github/sumidu/Slacker.jl?svg=true)](https://ci.appveyor.com/project/sumidu/Slacker-jl)
[![Codecov](https://codecov.io/gh/sumidu/Slacker.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/sumidu/Slacker.jl)
[![Coveralls](https://coveralls.io/repos/github/sumidu/Slacker.jl/badge.svg?branch=master)](https://coveralls.io/github/sumidu/Slacker.jl?branch=master)
[![Build Status](https://api.cirrus-ci.com/github/sumidu/Slacker.jl.svg)](https://cirrus-ci.com/github/sumidu/Slacker.jl)

A package that allows sending to slack. It uses a configuration file stored in the home directory of the user.
It allows for multiple name configurations, if several slack servers are used.

```
  using Slacker

  # replace the url with your incoming Webhook URL
  cfg = SlackConfig("https://hooks.slack.com/services/....", "JuliaBot", "#general", ":ghost:")

  addConfig(cfg)

  sendSlackMessage("Hi this is a Test from Slacker.")

```

Using Multiple servers


```
  using Slacker

  cfg1 = SlackConfig("url1", "JuliaBot", "#general", ":ghost:")
  cfg2 = SlackConfig("url2", "JuliaBot2", "@sumidu", ":smile:")

  addConfig(cfg, "server1")
  addConfig(cfg, "server2")

  sendSlackMessage("Hi this is a Test from Slacker to server1.", "server1")
  sendSlackMessage("Hi this is a Test from Slacker to server1.", "server2")

```

Changing the channel or Username of a configuration temporarily

```
  using Slacker

  cfg = loadConfig("server1")
  cfg.channel = "#random"
  cfg.user = "Julia Random Bot"
  cfg.icon_emoji = ":grinning:"

  sendSlackMessage("Hi this is a Test from Slacker to server1.", cfg)
```
