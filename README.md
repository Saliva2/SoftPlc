# SoftPlc [![Build Status](https://travis-ci.org/fbarresi/SoftPlc.svg?branch=master)](https://travis-ci.org/fbarresi/SoftPlc) [![Build status](https://ci.appveyor.com/api/projects/status/bl05dyhpr3ah76y3?svg=true)](https://ci.appveyor.com/project/fbarresi/softplc) [![Docker Pulls](https://img.shields.io/docker/pulls/fbarresi/softplc.svg)](https://hub.docker.com/r/fbarresi/softplc/)
Software PLC controlled over Web API

**How often did you need a PLC for testing, but you had none?**

This project aim to **end you pain** with test against PLC!

## How does it works

### Use it from source code or binary 
Build and Start the software (don't forget to copy the native library you need)

```shell
cd SoftPlc
dotnet restore
dotnet build
cp native\win\snap7.dll bin\Debug\netcoreapp2.0\snap7.dll
dotnet bin\Debug\netcoreapp2.0\SoftPlc.dll --plcPort=103 --urls="http://localhost:8080/"
```

Otherwise you can download and start the [latest release](https://github.com/fbarresi/SoftPlc/releases/latest) (i.e. with Powershell).

```shell 
Expand-Archive softplc1.0.41-amd64.zip.zip -DestinationPath c:/temp/softplc
cd c:/temp/softplc/
dotnet SoftPlc.dll --plcPort=103 --urls="http://localhost:8080/"
```

### Use it with docker
Pull the actual docker image for your platform [see available tags](https://hub.docker.com/r/fbarresi/softplc/tags/) and run it with the correct port binding. (Brand new MOBY support is included! Just select latest-win1809 tag.)

```docker
docker pull fbarresi/softplc:latest-linux
docker run -p 8080:80 -p 102:102 --name softplc fbarresi/softplc:latest-linux
```

Now you have:

- a Simulated PLC listening at port 102 ([see ISO-over-TCP protocol](https://tools.ietf.org/html/rfc1006))

- an API listening at http://localhost:8080/  (with Swagger included under http://localhost:8080/swagger ) in which you can __add__, __read__, __modify__ and __delete__ as many datablocks as you want


![SoftPlc API](https://github.com/fbarresi/SoftPlc/raw/master/img/SoftPlc_API.png "Api")


### Do you also need a PLC Client in your application?

Check my other repository [Sharp7](https://github.com/fbarresi/Sharp7) or [Sharp7Reactive](https://github.com/evopro-ag/Sharp7Reactive)


## Contribute

Whould you like to contribute? YES, Please! Just fork/star/watch this repo and submit a pull request!

## Credits

This software uses Snap7 as PLC server implementation.
For info please visit the official page: [http://snap7.sourceforge.net](http://snap7.sourceforge.net)
