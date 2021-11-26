---
title: DotNet on Raspberry pi
date: 2021-09-12 00:00:00 +0300
description: Notes on dotnet 5 and raspberry pi # Add post description (optional)
img: ./software.jpg # Add image post (optional)
tags: [git, github] # add tag
---

## what about package manager install

 For a developer or user, it's better to use a to install .NET on Linux. But for CI situations.

Downloads of binaries for dotnet are kept [here](https://dotnet.microsoft.com/download/dotnet) and

[dotNet 6 here](https://dotnet.microsoft.com/download/dotnet/6.0)


The steps to install are as follows:

1. Dependencies and requirements

See (https://docs.microsoft.com/en-gb/dotnet/core/install/linux)
2. Install SDK

```
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-6.0.100-rc.2.21505.57-linux-arm64.tar.gz -C $HOME/dotnet
```

3.
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet

## Installation via bash script

https://docs.microsoft.com/en-gb/dotnet/core/install/linux-scripted-manual#scripted-install

## Pipe and sudo bash a better way.

```dotnet
dotnetver='6.0'
Where are these files
# sdkfile=/tmp/dotnetsdk.tar.gz
aspnetfile=/tmp/aspnetcore.tar.gz

apt-get -y install libunwind8 gettext

```
## https://docs.microsoft.com/en-gb/dotnet/core/docker/build-container?tabs=windows

## Check runtime versions and SDK installed

Details on checking versions (https://docs.microsoft.com/en-gb/dotnet/core/install/how-to-detect-installed-versions?pivots=os-linux)

```
dotnet --list-sdks
dotnet --list-runtimes
```