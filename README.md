# Sample .NET Core application for Ubuntu Snappy

This example shows how to package a .NET Core application for execution on Ubuntu Snappy.

It uses the [snapcraft](https://developer.ubuntu.com/en/snappy/snapcraft/) tool to generate the snap package. You will need to install it:

```
$ sudo add-apt-repository ppa:snappy-dev/tools
$ sudo apt-get update
$ sudo apt-get install snapcraft
```

You also need to [install .NET Core](http://dotnet.readthedocs.org/en/latest/getting-started/installing-core-linux.html) on your Ubuntu box in order to build the sample.

The .NET Core app itself resides in `dnxhelloworld`. The Makefile in that directory will use the .NET Core `dnu` and `dnx` tools to build and publish the sample. When published, the app is a self-contained unit that includes all the necessary .NET Core runtime bits.

The `snapcraft.yaml` file contains all the metadata needed to assemble the snap. Check it out if you want to change the executable name, etc.

Build the snap:

```
$ snapcraft
```

Copy the generated snap to a Snappy machine:

```
$ scp dnx-sample_1.0_amd64.snap ubuntu@mysnappyvm.cloudapp.net:
```

On the Snappy machine, install the snap and run it:

```
$ sudo snappy install dnx-sample_1.0_amd64.snap --allow-unauthenticated
$ dnx-sample.hellodnx
```

