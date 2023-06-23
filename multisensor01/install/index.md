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

<form>
  <input type="radio" name="version" value="ms1_rev_1.0"> MS1 - Rev 1.0<br>
  <input type="radio" name="version" value="ms1_rev_1.1"> MS1 - Rev 1.1<br>

  <div id="sensor-options">
    <input type="radio" name="sensor" value="dfrobot_sen0395"> DFRobot SEN0395 Sensor<br>
    <input type="radio" name="sensor" value="hlk_sensor"> HLK Sensor<br>
    <input type="radio" name="sensor" value="seeed_studio_sensor"> Seeed Studio Sensor<br>
  </div>

  <input type="submit" value="Submit">
</form>



<script
  type="module"
  src="https://unpkg.com/esp-web-tools@9/dist/web/install-button.js?module"
></script>
<h3>Install for Home Assistant</h3>
<esp-web-install-button
  manifest="./ms01-ha-manifest.json"
></esp-web-install-button>