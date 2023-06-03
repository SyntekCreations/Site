---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: ESP32 MultiSensor 01
description: A ESP32 based device for a variety of presence and environmental sensors. 

# Author box
#author:
#    title: About Author
#    title_url: '#'
#    external_url: true
#    description: Author description

# Micro navigation
micro_nav: true

# Page navigation
#page_nav:
#    prev:
#        content: Previous page
#        url: '#'
#    next:
#        content: Next page
#        url: '#'
---

<body>
    <h2>Configuration</h2>
    <p>Dox have a lot of personalization options. Here you can go through every single one available in our theme and set it up properly.</p>
    <h3>Introduction</h3>
    <p><code>_config.yml</code> stores configuration data. Many of these options can be specified from the command line executable but it’s easier to specify them here so you don’t have to remember them.</p>
    <p>Please stop and re-run <code>jekyll serve</code> command after you change configuration file! Master configuration file contains global configurations and variable definitions that are read once at execution time. Changes made to <code>config.yml</code> during automatic regeneration are not loaded until the next execution.</p>
    <h2>Relative URLs</h2>
    <p>If you’re deploying to server where your site is not going to be in root directory, you should setup <code>baseurl</code> variable.</p>
    <p>For example, if your site is going to be stored on URL that looks like this - <code>http://example.com/project</code>, you’ll have to update your <code>baseurl</code> variable and it should look like this:</p>
    <div class="example">
    ```
    dox:
        baseurl: /project
    ```
    </div>
    <h3>Build site with environment variable!</h3>
    <p>When you run <code>jekyll serve</code>, your <code>baseurl</code> variable shouldn’t render at all in any pages.</p>
    <p>We’ll set Jekyll to only render <code>baseurl</code> variable when its environment is set to production.</p>
    <p>So then, how do you get the <code>baseurl</code> variable to only show up on a production environment? When building your Jekyll project with <code>jekyll build</code>, you’ll want to prefix it with <code>JEKYLL_ENV=production</code> so the complete command looks like this one: <code>JEKYLL_ENV=production jekyll build</code></p>

</body>
