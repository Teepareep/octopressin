---
layout: post
title: "It seems your ruby installation is missing psych"
date: 2013-04-14 10:28
comments: true
categories: 
published: false
---

I have been recieving the following warning no matter how I reinstall rvm and ruby:

```
# gem --version
/usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/yaml.rb:56:in `<top (required)>':
It seems your ruby installation is missing psych (for YAML output).
To eliminate this warning, please install libyaml and reinstall your ruby.
1.8.25
```

I tried a dozen different fixes aimed at the libyaml part of the error before I broke down and did:

```
gem install psych
```

Was that so hard, brain?
