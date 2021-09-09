
# Node-RED-IOT

<img src="https://avatars0.githubusercontent.com/u/28384526?s=200&v=4" alt="Wago" height="150" align="middle">
<img src="https://avatars3.githubusercontent.com/u/5375661?s=200&v=4" alt="Node-Red" height="150" align="middle">

</br>
</br>


[![DockerHub stars](https://img.shields.io/docker/stars/wagoautomation/node-red-iot.svg?flat&logo=docker "DockerHub stars")](https://hub.docker.com/r/wagoautomation/node-red-iot)
[![DockerHub pulls](https://img.shields.io/docker/pulls/wagoautomation/node-red-iot.svg?flat&logo=docker "DockerHub pulls")](https://hub.docker.com/r/wagoautomation/node-red-iot)

The image is based on the original Node-RED image (see: https://hub.docker.com/r/nodered/node-red) and contains the following pre-installed Node modules:
- node-red-contrib-iiot-opcua
- node-red-contrib-modbustcp
- node-red-dashboard
- node-red-contrib-telegrambot
- node-red-contrib-bacnet

## Tag schema
The tag has a three-part structure:

\<Node-RED version\> - \<Node version\> - \<vBuild version\>  
e.g. : 1.3.6-12-v2.3.0

| **Tag**                    | **Node-RED** | **Node** | **Build** |
|----------------------------|--------------|----------|-----------|
| 1.3.6-12-v2.3.0            |    1.3.6     |    12    |   v2.3.0  |

>The two-part tags always represent the latest version of a Node-RED Node bundle.     
  

## Image Variations
The Node-RED images come in different variations and are supported by manifest lists (auto-detect architecture).
This makes it more easy to deploy in a multi architecture Docker environment. 

The tag naming convention is `<node-red-version>-<node-version>-<build-version>`, where:
- `<node-red-version>` is the Node-RED version.
- `<node-version>` is the Node JS version.
- `<build-version>` is build version of image and is optional


For example - to run the latest Node-RED bundle with Node-RED version 1.3.6 and Node version 12, you would run
```
docker run -it -p 1880:1880 -v node_red_data:/data --name mynodered wagoautomation/node-red-iot:1.3.6-12
```

For more detailed information about the original Node-RED docker image see [docker guide](https://nodered.org/docs/getting-started/docker).

For general information about Node-RED please visit the [website](https://nodered.org/).

This project is available on [github](https://github.com/WAGO/node-red-iot).