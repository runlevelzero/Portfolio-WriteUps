# Getting started with PyWlroots

I initially had some issues getting [pywlroots](https://github.com/flacjacket/pywlroots) working on my machine. For whatever reason, installing it with pip just didn't work for me. So I wanted to write a kind of how to guide on how I got it working. If this isn't the right way on how to do it, please let me know by raising an issue [here](https://github.com/runlevelzero/Portfolio-WriteUps/issues) and I will get around to fixing this documentation

## 1. Installing dependencies
This guide will mainly focus on installing this on a debian based machine so all of the commands will be for a system that uses apt

**Other Dependencies**
These are some of the dependencies I found in the travis CI file for pywlroots, I will audit these later to see which ones are the bare necessities

`sudo apt install libdrm-dev libinput-dev libgbm-dev libgles2-mesa-dev libxcb1-dev libxcb-composite0-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-xfixes0-dev libxcb-xinput-dev libxcb-render0-dev libxkbcommon-dev ninja-build libwayland-dev libwlroots-dev`

**Python**
You will need Python 3 for this library to work as well as pip

`sudo apt install python3 python3-pip`

You can make sure that python was installed by running this command

`python3 --version`

If your python version is 3.7 or under, the setup.cfg file mentions that you have an additional dependency

