# RGL.gg Comp TF2 Server Guide

I've made this guide in order to help out people trying to configure their TF2 server for competitive play. I know from experience many of the resources and steps can be unclear and hidden, so I've consolidated the information in hopefully an easy-to-follow guide.

This guide does not go over how to self-host, it is under the assumption you are either renting a server or know how to host an SRCDs server

#### Contents

[Installing Sourcemod](https://github.com/Av3r4ge/rgl-comp-server-guide?tab=readme-ov-file#installing-sourcemod)

[Installing Required Plugins](https://github.com/Av3r4ge/rgl-comp-server-guide?tab=readme-ov-file#installing-required-plugins)

[Setting Up Your cfgs](https://github.com/Av3r4ge/rgl-comp-server-guide?tab=readme-ov-file#setting-up-your-cfgs)

[Installing Optional Plugins](https://github.com/Av3r4ge/rgl-comp-server-guide?tab=readme-ov-file#optional-plugins)

[Miscellaneous](https://github.com/Av3r4ge/rgl-comp-server-guide?tab=readme-ov-file#miscellaneous)

***

## Installing Sourcemod

The first step to be able to start installing all plugins required is installing Metamod and Sourcemod to your server. 

You first need to install Metamod:Source in order to be able to download Sourcemod.

Download [Metamod:Source](https://www.sourcemm.net/downloads.php?branch=stable) respective to which operating system your provider uses. If you are not sure, it's likely that your server provider runs their servers on linux. After downloading it you should find the `addons` folder inside, extract that folder into `tf/` so you have `tf/addons`

After installing Metamod:Source then download [Sourcemod](https://www.sourcemod.net/downloads.php?branch=stable) respective to which OS your server uses. You should find `addons` and `cfg` inside, extract those the same into `tf/`



#### Testing Installation

After installing, restart your server and type in `sm version` into your server's console. If it shows the sourcemod version you're good to go.

If the command is missing you likely installed the files into the wrong location or used the wrong version of Metamod or Sourcemod.

***

## Installing Required Plugins



#### RGL Server Resources Updater

RGL requires certain plugins to be present on the server in order to ensure competitive integrity. You can download their plugins from the offical RGL.gg repostiory [here](https://github.com/RGLgg/server-resources-updater). They have installation steps on their page. You should keep this plugin up to date, your server will notify you when a new version is released.

#### DemosTF Uploader

Head over to [demos.tf/upload](https://demos.tf/upload) and login with your account. You will plugin installation steps and your API key. **Firstly save your API key because we'll need it later when setting up your server config**.

You will now need to download the cURL extension from the installation steps, it should lead you [here](https://github.com/sapphonie/SM-neocurl-ext). Download the zip file from the latest releases. You will need to extract these files in your sourcemod folder in `/tf/addons/sourcemod/`

Now you need to download the plugin from the installation steps, it should lead you to [here](https://github.com/demostf/plugin). Drag the .smx file into `/tf/addons/sourcemod/plugins/` and you should be good to go

#### LogsTF Uploader

Downloading the logs.tf uploader is similar to downloading the demos.tf uploader. Head over to [logs.tf/uploader](https://logs.tf/uploader) and log in. **Again, save your API key from logs.tf because we will need it when configuring our server**. Keep this API key safe as people can upload logs under your account whether they may be malicious or not.

Now you need to choose which plugin you will use for automated upload, for this guide we'll use LogsTF plugin by F2. There are three plugins you have to download [here](https://www.teamfortress.tv/13598/?page=1#post-1). Download MedicStats, SupStats2, and LogsTF. You should have an .smx file from each. Drag these files into `/tf/addons/sourcemod/plugins/`



After uploading all of these you should be good for all the required plugins your server needs.

***

## Setting up your .cfgs

In this repository there is a basic [server.cfg](/configs/server.cfg) file. Anything in the server.cfg is automatically loaded when the server is started up. We will use this to setup the server's basic config file.

In this file there are lines you should change before you start your server with it. The most critical ones are your server passwords and API keys

#### Passwords

Let's start by editing `server.cfg` and changing `sv_password`, `rcon_password`, and `tv_password`

Your `sv_password` controls what password is needed for clients to connect to your server

`tv_password` controls what password is needed to connect to SourceTV

`rcon_password` your RCON password is what allows you to run commands remotely to your server's console such as executing CFGs and changing maps. **KEEP THIS ONE SAFE**

#### API Keys

Remember the keys we saved before from our demos.tf and logs.tf page? We import these here.

in your `server.cfg` edit `logstf_apikey` and paste your logs.tf key within the quotes, do the same with your demos.tf in `sm_demostf_apikey`

#### SourceTV

Make sure your STV port is set correctly, the default is 27020 but you may need to change it depending on what ports your provider has given you. If you do not have an extra port allocated you should contact your provider to assign you an extra port for STV

To change the STV Port, go to your `server.cfg` and uncomment the `tv_port` line by deleting the double slashes. You can then change the port by changing the value.

#### FastDL (Optional)

FastDL is a way for people to download content through an HTTP server automatically when connecting to a server. Source has a way to automatically share files to the client but it is extremely slow. This is very useful if people don't have a map and are connecting for the first time.

The directory of the webserver should match to the servers `tf/` directory. (for example it should contain the directories `tf/maps` and `tf/materials` from that link 

If your host provides you with a fastDL server or you are hosting one you can add it to your `server.cfg` file like this

```
sv_allowdownload 1
sv_allowupload 1
sv_downloadurl "http://exampleFastDL.com/fastdl/tf/"
```

At the time of writing this, [sapphonie](https://github.com/sapphonie) provides a way for people to use their FastDL server. You can use theirs by copy and pasting this into your server.cfg

```
sv_allowdownload 1
sv_allowupload 1
sv_downloadurl "https://sappho.io/files/tf/"
```

They also have a way to upload new maps to their server by going to https://sappho.io/files/tf/

***

## Optional Plugins

## SoapDM

Many servers have SoapDM in their pregrame before readying up. This is very easy to setup and all it requires is just installing the plugin. You can download the plugin [here](https://github.com/sapphonie/SOAP-TF2DM).
After downloading, inside the zip file there will be an `addons` and a `cfg` folder. Drag these folders to your `tf/` directory of your server to install it.

SoapDM should work after your next restart. It will automatically unload when MGE is active or the round starts if you're in tournament mode.

## MGE

MGE is also pretty straight forward to setup like SoapDM. You can download the plugin [here](https://github.com/sapphonie/MGEMod?tab=readme-ov-file).  Download the zip file and you should see an `addons` folder and a `maps` folder. Drag these folders to your `tf/` directory of your server to install it.

MGE will automatically load when it loads to one of the mge maps included in the maps folder.

---

## Miscellaneous

#### Allowing for SDR support

SDR is Valve's own network relay that can be enabled on source servers. This can be useful for players with bad routing to your server. To enable Valve SDR you need to add `-enablefakeip` to your servers launch options. Most hosting providers do not allow you to change your launch options of your server.

On your next reboot your server will request an IP. You can test to see if SDR is enabled by typing `status` in console. 

``udp/ip  : ** Valve IP **  (local: 0.0.0.0:27015)  (public IP from Steam: ** Your Server's IP** )``

If your main server IP is different, then it works. You can use this as your connect IP and it'll use valve's routing.

#### MOTD

This is the thing people see when you first join the server. To edit your motd, go to your `tf/cfgs/` and create a `motd.txt` file. In this file you can create HTML, plain text, or paste a link to it.