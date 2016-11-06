---
layout: post
title: open-source firmware for canon camera
date: 2012-02-17 10:00:10.000000000 +01:00
---
Free open-source software always fascinates me. You have a product that was designed and produced by an industrial manufacturer and then you have a bunch of free-minded people that just decide to take this peace of plastic -- or metal -- and turn it into something different; supercharging/pimping it. In an earlier [post]({%link _posts/2009-11-08-open-source-firmware-for-your-mp3-player.markdown %}) I've written about <a href="http://www.rockbox.org/">Rockbox</a>, which managed to free some limited devices from their simplistic firmware and added lots of features and the ability to play all kinds of other audio formats that were not playable before because of weird music industry politics.

<img alt="" src="http://3.bp.blogspot.com/_T_9GqO5gINk/TAa_19DzXOI/AAAAAAAADM8/rE5ylm3NyhU/s1600/chdk.png" title="CHDK logo" class="alignnone" width="155" height="155" />

<a href="http://chdk.wikia.com/wiki/CHDK">CHDK</a> is a bit different in that it only adds some features to your camera and runs beside the original firmware. Like Rockbox it adds another format, in this case RAW, and it makes a whole lot of other ways to use the device. CHDK gives you more control over all details of the picture generation too and allows you a closer look at the inner workings of a camera. You can control the details of exposure and bracketing. I'm curios about how you can use another feature; scripts. You can write scripts that tell the camera when and how to make pictures. If you combine this with the motion detection, you get a pretty sophisticated camera. Maybe, I'll use it for some timelapse experiments. It seems like that should be easy. It's also possible to make <a href="http://novocor.blogspot.com/2010/06/chdk-canon-hack-development-kit-review.html">HDR pictures</a> (blog post in German) like this.

<img src="http://images1.wikia.nocookie.net/__cb20071013223061/chdk/images/9/9c/Raw.jpg" alt="OSD view augmented with CHDK elements" />

Installing the firmware is not soo easy, but doable. Find your <a href="http://chdk.wikia.com/wiki/FAQ#Q._What_camera_models_are_supported_by_the_CHDK_program.3F">camera's installation page</a>, download the modified firmware, extract it on a SD-card, change to playback mode, press the firmware-update entry in the menu and be happy. Upon restart the firmware is gone; it's only temporarily loaded to memory.

Have Fun!
