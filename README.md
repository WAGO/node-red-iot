# node-red-iot
# tag 2.0.0 contains the first official Node-Red Version

## Build your own Docker Container
### Node-Red on Wago 'PFC 200 G2' and 'TP 600'.
 
Usage to start Container on arm Device

docker run -d --name wago-node-red -p 1880:1880 -v ~/data:/root/.node-red wagopfc/node-red:tag


Usage to start Container on x86 Device  | Usage inside Browser

docker run -d --name wago-node-red -p 1880:1880 -v ~/data:/root/.node-red -v /usr/bin/qemu-arm-static:/usr/bin/qemu-arm-static wagopfc/node-red:tag
   
If using x86 please install qemu support on your System.   
Watch: https://ownyourbits.com/2018/06/27/running-and-building-arm-docker-containers-in-x86/ 

   
Afterwards you can use Node-red in your local Browser.  
The database is be stored persistent inside the volume.
<h4>Node-red starts himself, be patient, start takes less then 1 minutes on Touch Panel 600. <h4>
<h5>(On PFC device start takes up to max. 1 minute.)  <h5/>
  
<h4>Please use tag 2.0.0 to get the extended Version including the official Node-Red Version.<h4/>

GitHub Repository to get Docker ipk file:
https://github.com/WAGO/docker-ipk
 
GitHub Repository Docker quickstart:
https://github.com/WAGO/pfc-documentation
