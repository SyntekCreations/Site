---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: ESP32 MultiSensor (MS01)
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
<h2>Install/Update your MultiSensor</h2>
<p>Follow the guide below to install the latest firmware on your MultiSensor</p>
<script
  type="module"
  src="https://unpkg.com/esp-web-tools@9/dist/web/install-button.js?module"
></script>
<h3>Install for Home Assistant</h3>
<esp-web-install-button
  manifest="https://firmware.esphome.io/esphome-web/manifest.json"
></esp-web-install-button>