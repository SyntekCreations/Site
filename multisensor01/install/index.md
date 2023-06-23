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

<style>
  body {
    font-family: Arial, sans-serif;
  }

  #software-form {
    width: 300px;
    margin-left: 20px;
    padding: 20px;
    background-color: #f0f0f0;
    border-radius: 5px;
  }

  h1 {
    text-align: center;
  }

  fieldset {
    border: none;
    margin: 10px 0;
  }

  legend {
    font-weight: bold;
    margin-bottom: 5px;
  }

  label {
    display: block;
    margin-bottom: 5px;
  }

  input[type="radio"] {
    margin-right: 5px;
  }
</style>

<h2>Install/Update your MultiSensor</h2>
<p>Follow the guide below to install the latest firmware on your MultiSensor ready for Home Assistant</p>

<h3>Select hardware revision and mmWave sensor</h3>
<form id="software-form">
  <fieldset>
    <legend>Hardware Revision</legend>
    <label><input type="radio" name="version" value="ms1_rev_1.0"> MS01 - Rev 1.0</label>
    <label><input type="radio" name="version" value="ms1_rev_1.1"> MS01 - Rev 1.1</label>
  </fieldset>

  <fieldset>
    <legend>mmWave Sensor Options</legend>
    <label><input type="radio" name="sensor" value="dfrobot_sen0395"> DFRobot SEN0395 Sensor</label>
    <label><input type="radio" name="sensor" value="hlk_sensor"> HLK Sensor</label>
    <label><input type="radio" name="sensor" value="seeed_studio_sensor"> Seeed Studio Sensor</label>
  </fieldset>
</form>


<h3>Install</h3>
<p class="button-row" align="left">
  <esp-web-install-button></esp-web-install-button>
</p>


<script
  type="module"
  src="https://unpkg.com/esp-web-tools@9/dist/web/install-button.js?module"
></script>

<script>
  const versionRadios = document.getElementsByName("version");
  const sensorRadios = document.getElementsByName("sensor");
  const button = document.querySelector("esp-web-install-button");

  // Add event listeners to version and sensor radios
  for (let i = 0; i < versionRadios.length; i++) {
    versionRadios[i].addEventListener("change", handleSelectionChange);
  }
  for (let i = 0; i < sensorRadios.length; i++) {
    sensorRadios[i].addEventListener("change", handleSelectionChange);
  }

  // Function to handle selection change
  function handleSelectionChange() {
    const selectedVersion = document.querySelector('input[name="version"]:checked').value;
    const selectedSensor = document.querySelector('input[name="sensor"]:checked').value;
    let fileName;

    // Generate the software file name based on selected options
    if (selectedVersion === "ms1_rev_1.0") {
      if (selectedSensor === "dfrobot_sen0395") {
        fileName = "MS1-Rev1.0-SEN0395-manifest.json";
      } else if (selectedSensor === "hlk_sensor") {
        fileName = "MS1-Rev1.0-HLK-manifest.json";
      }
    } else if (selectedVersion === "ms1_rev_1.1") {
      if (selectedSensor === "dfrobot_sen0395") {
        fileName = "MS1-Rev1.1-SEN0395-manifest.json";
      } else if (selectedSensor === "seeed_studio_sensor") {
        fileName = "MS1-Rev1.1-Seeed-manifest.json";
      } else if (selectedSensor === "hlk_sensor") {
        fileName = "MS1-Rev1.1-HLK-manifest.json";
      }
    }

    // Set the manifest attribute of the button
    if (fileName) {
      button.manifest = `./${fileName}`;
    }
  }
</script>