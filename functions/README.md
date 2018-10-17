## Introduction

In this guide, we'll show you a few simple steps to launch an Oracle Linux instance on Oracle Cloud Infrastructure, and then proceed to launch your Fn Functions server & run your cloud functions. The path that we will take is as follows:

 - Launch your Oracle Linux instance in the Oracle cloud
 - Install Oracle Container Runtime for Docker
 - Install the Fn Functions Server
 - Configure and run your Oracle Code Card Fn functions

## Create an Oracle Linux instance on the Oracle Cloud Infrastructure
Follow [these instructions](oci.md) to create an Oracle Linux instance and the come back after you are done.

## Configuring your Fn Server

Your Oracle Linux instance is now running, and ready to be configured to host your cloud functions.

### Install and configure Docker

While connected to your Oracle Linux instance, run the following commands to install and configure the Docker container runtime.

```
$ sudo yum install docker-engine -y
$ sudo usermod -aG docker opc
$ sudo systemctl enable docker
$ sudo systemctl start docker
```

Before proceeding further, logout of the current SSH session, & then reconnect to your Oracle Linux instance and log back in vis SSH. _This is to ensure group membership configured in the previous step is correctly applied and in effect._
Once you have reconnected to the instance, run the following command to install the Fn CLI tool (this will download a shell script and execute it).

### Configure Oracle Linux for Fn

```
$ sudo curl -LSs https://raw.githubusercontent.com/fnproject/cli/master/install | sh
```

At completion, the installation will output the Fn CLI version - per the below example output.

```
$
fn version 0.4.155
        ______
       / ____/___
      / /_  / __ \
     / __/ / / / /
    /_/   /_/ /_/`
$
```

### Start your Fn Server

Run the following command which will start Fn in single server mode, using an embedded database and message queue.

```
$ sudo /usr/local/bin/fn start &

...
$ time="2018-09-10T07:58:06Z" level=info msg="available cpu" availCPU=2000 totalCPU=2000
$ time="2018-09-10T07:58:06Z" level=info msg="sync and async cpu reservations" cpuAsync=1600 cpuAsyncHWMark=1280 cpuSync=400

        ______
       / ____/___
      / /_  / __ \
     / __/ / / / /
    /_/   /_/ /_/
        v0.3.548

$ time="2018-09-10T07:58:06Z" level=info msg="Fn serving on `:8080`" type=full
```

Your Fn server is now instantiated and running in the background.

## Configure and run your Fn functions

Functions are small but powerful blocks of code that generally do one simple thing. Forget about monoliths when using functions, just focus on the task that you want the function to perform. Our CLI tool will help you get started super quickly.

To create a hello world function, run the following command.

```
$ fn init --runtime go hello
```

This will create a simple function in the directory hello, so let's cd into it:

```
$ cd hello
```

### Run your function locally

```
$ fn run
Building image hello:0.0.1 .....................................
{"message":"Hello World"}
$
```

### Deploy your functions to your local Fn server

```
$ fn deploy --app myapp --local
Bumped to version 0.0.2
Building image hello:0.0.2 .......
Updating route /hello using image hello:0.0.2...
$
```

Now you can call your function locally using curl:

```
curl http://localhost:8080/r/myapp/hello
```

or, using the fn client:

```
fn call myapp /hello
```

or in a browser: http://`linux-instance-public-ip`:8080/r/myapp/hello

That's it! You just deployed your first function and called it. You are now ready to configure your Code Card to access your cloud function!
