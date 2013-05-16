---
layout: post
title: "install jekyll bootstrap"
description: "install jekyll bootstrap note"
category: lessons
tags: [jekyll, bootstrap]
---
{% include JB/setup %}

## Install Jekyll-Bootstrap

## Run Jekyll Locally
  gem install jekyll
  git clone Jekyll-Bootstrap
  cd Jekyll-Bootstrap
  jekyll serve [port]

## Create a Post
  rake post title="title_name"

## Create a Page
  rake page name="page_name.md"
  rake page name="pages/page_name"

## Publish 
  git add .
  git commit -m "message"
  git push origin master

## Customize
  + Themes
    rake theme:install git="theme git path"
    rake theme:switch name="theme name"
  + Blog Configuration
    _config.yml



