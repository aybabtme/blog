---
layout: post
title: "Keeping an Heroku instance alive"
date: 2012-12-04 20:13
comments: true
categories: [hack, heroku]
---
I used to have a Linode VM.  I still have a Linode VM.  But I regularly
fuck up my setup (lock myself out, get lost in between nginx and
apache's install and config files, mess up my iptables rules, etc), so 
it's not the best platform to use when I want to explore stuff about 
web development.

Heroku is great for that, you can get your instance for free and the
deployment is a breeze.  But your free instance (or dyno) is turned off
after every hour of inactivity on your website.  This is quite annoying.
It means the visitor coming an hour after the last visitor will see the
page load for a dozen of seconds before being served anything, while heroku
turns your dyno back online.

So here's a pretty trivial solution to this annoyance:

> CRON JOBS!

Yayyyyy!  Create a small script that gets a pages from your app every
hour, and put that in your `/etc/cron.hourly/` folder.  Too simple!

So I did this little script:

``` ruby heroku-keep-alive
#!/usr/bin/env ruby

require 'net/http'

APPS = [
  "aybabtme"
]

def get_app_uri( app_name )
  heroku_app = "http://#{app_name}.heroku.com/index.html"
  URI.parse(heroku_app)
end

def wake_up_instance_at_uri( uri )
  res = Net::HTTP.get_response(uri)
  if res.code == "301"
    res = Net::HTTP.get_response(URI.parse(res.header['location']))
  end
end

APPS.each do |app_name|
  uri = get_app_uri app_name
  wake_up_instance_at_uri uri
end
```
Just fill in your app names in the `APPS` array, save it somewhere and 
``` bash
$ chmod +x /path/to/heroku-keep-alive
$ crontab  # will overwrite any previous jobs
0 * * * * /path/to/heroku-keep-alive
```
Press `Ctrl+D`. Confirm it's been added to your cron jobs:
``` bash
$ crontab -l
0 * * * * /path/to/heroku-keep-alive
```
Yayyy, victory! I've, ironically, put this cron job on my Linode,
since it's always turned on.  You could put that on your *nix box
 at home, given that it should be turned on most of the time. 
 
Actually, all you really need is to `wget` your index (`curl` won't do 
it, heroku has a permanent redirect to your instance and `curl` won't 
follow it), but that would be _too_ simple. Hey, where's the fun if
there's no code at all?
