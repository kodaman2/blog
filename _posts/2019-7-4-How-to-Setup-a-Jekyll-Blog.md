---
layout: post
title: How to Setup a Jekyll Blog and link to Dev.to
---

I am in the process of writing a series, and while I have awesome tools like scrivener for book writing, it doesn't work quite well with markdown. In this guide I will show you how to setup jekyll with minimal effort.


Jekyll-Now [Quick Start](https://github.com/barryclark/jekyll-now#quick-start) 
- Fork [jekyll-now](https://github.com/barryclark/jekyll-now)
- Rename repo to username.github.io under settings. If this is not your main site, you can also just name it whatever. For example my main github.io is used as a portfolio, so I just renamed mine to "blog". Github pages will automatically serve it at kodaman2.github.io/blog.

If this is your github.io page, then it will be ready to view with a demo post. If this is not your github.io repo, then go to settings, scroll down to Github Pages, and select the branch. Once that's done you should be able to see your site.

## Configure _config.yml

Below are the settings I changed:
name, description, avatar, github, twitter, url, baseurl, theme.

The file is heavily commented, so it was easy to modify. The baseurl is necessary because is not my main github.io site as you can read in the comments. Check the changes [_config.yml](https://github.com/kodaman2/blog/blame/master/_config.yml) if you have problems.

It doesn't take too long for the site to sync with the repo changes.

## Publish posts to Dev.to with RSS Feed

In https://dev.to/settings/publishing-from-rss enter your site rss feed, if you are using github pages it would be username.github.io/feed or username.github.io/repo_name/feed hit the update button, and then the fetch button on top.

If everything worked you should see the "You are up and running" demo post. Note that articles are not published, and are synced as drafts from the RSS feed.

## Publish new Posts

To make new posts go to _posts folder, and create a new md file. Ex: year-month-day-title.md. 

Remember to add the front matter, check the demo post. [front-matter-docs](https://jekyllrb.com/docs/front-matter/)

```
---
layout: post
title: Blogging Like a Hacker
---
```

Hope you enjoyed this quick and easy guide to build your own blog, and publish on dev.to at the same time. Thanks for reading.