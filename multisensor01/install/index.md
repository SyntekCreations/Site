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

<h3>Select board version and sensor</h3>
<form id="software-form">
  <fieldset>
    <legend>Version</legend>
    <input type="radio" name="version" value="ms1_rev_1.0"> MS1 - Rev 1.0<br>
    <input type="radio" name="version" value="ms1_rev_1.1"> MS1 - Rev 1.1<br>
  </fieldset>

  <fieldset>
    <legend>Sensor Options</legend>
    <input type="radio" name="sensor" value="dfrobot_sen0395"> DFRobot SEN0395 Sensor<br>
    <input type="radio" name="sensor" value="hlk_sensor"> HLK Sensor<br>
    <input type="radio" name="sensor" value="seeed_studio_sensor"> Seeed Studio Sensor<br>
  </fieldset>
</form>

<h3>Install for Home Assistant</h3>
<p class="button-row" align="left">
  <esp-web-install-button></esp-web-install-button>
</p>


<script
  type="module"
  src="https://unpkg.com/esp-web-tools@9/dist/web/install-button.js?module"
></script>


<script>
  const softwareForm = document.getElementById("software-form");
  const button = document.querySelector("esp-web-install-button");

  softwareForm.addEventListener("submit", function(event) {
    event.preventDefault(); // Prevent form submission

    const versionRadios = document.getElementsByName("version");
    const sensorRadios = document.getElementsByName("sensor");
    let selectedVersion, selectedSensor;

    // Find the selected version
    for (let i = 0; i < versionRadios.length; i++) {
      if (versionRadios[i].checked) {
        selectedVersion = versionRadios[i].value;
        break;
      }
    }

    // Find the selected sensor
    for (let i = 0; i < sensorRadios.length; i++) {
      if (sensorRadios[i].checked) {
        selectedSensor = sensorRadios[i].value;
        break;
      }
    }

    // Generate the software file name based on selected options
    let fileName;
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
      console.log("Installing software with file name:", fileName);
    } else {
      console.log("Please select a version and sensor option.");
    }
  });
</script>