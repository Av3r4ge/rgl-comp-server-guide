# RGL.gg Comp TF2 Server Guide

I've made this guide in order to help out people trying to configure their TF2 server for competitive play. I know from experience many of the resources and steps can be unclear and hidden, so I've consolidated the information in hopefully an easy-to-follow guide.

This guide does not go over how to self-host, it is under the assumption you are either renting a server or know how to host an SRCDs server

***

## Installing Sourcemod

The first step to be able to start installing all plugins required is installing Metamod and Sourcemod to your server. 

You first need to install Metamod:Source in order to be able to download Sourcemod.

Download [Metamod:Source](https://www.sourcemm.net/downloads.php?branch=stable) respective to which operating system your provider uses. If you are not sure, it's likely that your server provider runs their servers on linux. After downloading it you should find the `addons` folder inside, extract that folder into `tf/` so you have `tf/addons`

After installing Metamod:Source then download [Sourcemod](https://www.sourcemod.net/downloads.php?branch=stable) respective to which OS your server uses. You should find `addons` and `cfg` inside, extract those the same into `tf/`

#### Testing Installation

After installing, restart your server and type in `sm info` into your server's console. If it shows the sorucemod version you're good to go.

If you can't run the command you likely installed the files into the wrong location or used the wrong version of Metamod/Sourcemod.

***

## Installing Required Plugins

RGL requires certain plugins to be present on the server in order to ensure competitive integrity.