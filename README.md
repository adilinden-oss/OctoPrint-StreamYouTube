# OctoPrint-YouTubeLive

## Overview 

Plugin that adds a tab to OctoPrint for viewing, starting, and stopping a YouTube Live stream. 

**Credits:**

Based on the work by 

- Alex Ellis found [here](https://blog.alexellis.io/live-stream-with-docker/)
- jneilliii [YouTube Live](https://plugins.octoprint.org/plugins/YouTubeLive/) plugin found [here](https://github.com/jneilliii/OctoPrint-YouTubeLive)

<img src="https://raw.githubusercontent.com/adilinden-oss/octoprint-youtubelive/adilinden/tab_screenshot.jpg">

## Requirements for Streaming

To stream the OctoPrint webcam [Docker](https://www.docker.com/) containers are required. Install `docker` and the [adilinden/rpi-ffmpeg](https://cloud.docker.com/repository/docker/adilinden/rpi-ffmpeg) ([source](https://github.com/adilinden-oss/docker-rpi-ffmpeg)) and [adilinden/rpi-stream](https://cloud.docker.com/u/adilinden/repository/docker/adilinden/rpi-stream) ([source](https://github.com/adilinden-oss/docker-rpi-stream)) images.

Using `ssh` access the OctoPi and install `docker`

    curl -sSL https://get.docker.com | sh
    sudo usermod pi -aG docker
    sudo reboot

Pull the `adilinden/rpi-stream` image

    docker pull adilinden/rpi-stream:latest

Test streaming by running the container manually, the following should work (repace the placeholders with your personal YouTubeLive account values)

    docker run -ti --rm --privileged --name YouTubeLive adilinden/rpi-stream:latest octopi-youtubelive http://<IP>:8080/?action=stream rtmp://a.rtmp.youtube.com/live2 xxxx-xxxx-xxxx-xxxx 

## Setup

Unless the plugin is made available in the official OctoPrint [PluginRepo](https://plugins.octoprint.org/) installation can be performed via these two methods

1. Open the plugin repository in the Plugin Manager's settings dialog, click on "Get more..." and enter the `https://github.com/adilinden-oss/octoprint-youtubelive/archive/adilinden.zip` URL in the "... from URL" box. Click the Install button to complete the installation.

2. Access the OctoPi command line and run the `~/oprint/bin/pip install https://github.com/adilinden-oss/octoprint-youtubelive/archive/adilinden.zip` command.

Pull up the **YouTube Live Settings** in the OctoPi settings panel

- Enter your Youtube channel id from your YouTube accounts [advanced account settings](http://www.youtube.com/account_advanced)
- Enter your YouTube Live server URL and stream name/key from your [live streaming dashboard](https://www.youtube.com/live_dashboard)
- Enter the fully qualified URL for your webcam stream, which typically something like `http://<IP>:8080/?action=stream` (Example: `http://192.168.1.34:8080/?action=stream`).

<img src="https://raw.githubusercontent.com/adilinden-oss/octoprint-youtubelive/adilinden/settings_screenshot.jpg">
