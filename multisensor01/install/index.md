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
    margin: 0 auto;
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
<p>Follow the guide below to install the latest firmware on your MultiSensor</p>

<h3>Select board version and sensor</h3>
<form id="software-form">
  <fieldset>
    <legend>Version</legend>
    <label><input type="radio" name="version" value="ms1_rev_1.0"> MS1 - Rev 1.0</label>
    <label><input type="radio" name="version" value="ms1_rev_1.1" checked> MS1 - Rev 1.1</label>
  </fieldset>

  <fieldset>
    <legend>Sensor Options</legend>
    <label><input type="radio" name="sensor" value="dfrobot_sen0395" checked> DFRobot SEN0395 Sensor</label>
    <label><input type="radio" name="sensor" value="hlk_sensor"> HLK Sensor</label>
    <label><input type="radio" name="sensor" value="seeed_studio_sensor"> Seeed Studio Sensor</label>
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
  const sensorOptions = document.getElementById("sensor-options");

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

  // Add event listener to version radios to toggle Seeed Studio Sensor option
  const versionRadios = document.getElementsByName("version");
  for (let i = 0; i < versionRadios.length; i++) {
    versionRadios[i].addEventListener("change", function() {
      if (this.checked && this.value === "ms1_rev_1.0") {
        // Hide Seeed Studio Sensor option for MS1 - Rev 1.0
        sensorOptions.querySelector('input[value="seeed_studio_sensor"]').style.display = "none";
      } else {
        // Show Seeed Studio Sensor option for other versions
        sensorOptions.querySelector('input[value="seeed_studio_sensor"]').style.display = "block";
      }
    });
  }
</script>