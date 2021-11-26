
## Jetson nano and dotnet

Jetson is an ARM64 device so any of the  linux Arm64 binaries should work and the build process
should be pretty much the same. In fact scripts for raspberry pi should work with minimal tweaking.

## Jetson Nano headless fresh setup (WiFi, SSH and VNC)


### Enable desktop Sharing


 Enabling Desktop Sharing

* Install vino

```$ sudo apt install vino
```

* Open the schema in nano editor

```$ sudo nano /usr/share/glib-2.0/schemas/org.gnome.Vino.gschema.xml
```

* add the following key into the XML file

```xml
 <key name='enabled' type='b'>
    <summary>Enable remote access to the desktop</summary>
    <description>
      If true, allows remote access to the desktop via the RFB
      protocol. Users on remote machines may then connect to the
      desktop using a VNC viewer.
    </description>
    <default>false</default>
  </key>
```
ctrl shift v to paste

If not installed need the header files provided by -dev packages. So install libglib2.0-dev Install libglib2.0-dev, by clicking that link or by running:

```xml
sudo apt-get update && sudo apt-get install libglib2.0-dev
```

Then recompile the schema

sudo glib-compile-schemas /usr/share/glib-2.0/schemas

This dont work  .....



## install editor

Nano editor is missing needed
To install
First, open the terminal and update the apt repositories with the command:

```linux
sudo apt update
sudo apt install nano
```

## Install curl
sudo apt install curl

## Purging Libre Office
This step is rather optional, but if you want to get some extra space and do not intend to use the Nano as a desktop computer, we suggest some purging.

## Purge libre office (gain approximately 250 MB extra)

sudo apt remove --purge libreoffice* -y
sudo apt-get clean -y
sudo apt autoremove -y
sudo apt-get update

## Fix graphics

May be needed.

## Docker Config

* run docker without sudo

sudo usermod -aG docker your_username
* update Docker

sudo apt-get --only-upgrade install docker.io

##  Install .NET Core on the Jetson Nano

    1. Download the latest (download required version of [ARM64 binaries, tar.gz](https://dotnet.microsoft.com/download/dotnet/) file)
    2. tar extract files to a suitable folder
    2. Add paths to bash profile

This can be achieved with a script ....

## Verify build of dotnet

`dotnet --info`

### Build test dotnet application

* On Jetson

```
dotnet new console -n hello-jetson-nano
cd hello-jetson-nano/
dotnet run
```

Once build You can use

```
dotnet bin/Debug/netcoreapp3.0/hello-jetson-nano.dll
```

### What about remote build and run i.e build on windows run on Jetson

...

## Issues

Ubuntu 18.04 (Jetson Nano) Xrdp Session Ends After Login



## Resource

(https://blog.headforcloud.com/2019/04/03/jetson-nano-a-quick-start-with-.net-core-3/)
)(https://www.forecr.io/blogs/programming/get-started-with-net-core-on-nvidia-jetson-nano-xavier-nx-modules)

[DeepStream](https://docs.nvidia.com/metropolis/deepstream/dev-guide/index.html#page/DeepStream_Development_Guide)

[Getting Started with NVIDIA Jetson Nano: Object Detection]https://www.youtube.com/watch?v=yZz-4uOx_Js
