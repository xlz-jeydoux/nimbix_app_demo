# introduction

this repository is the starting point to create a App in Nimbix cloud.
Major steps are:
  - git repository with Dockerfile, AppDef.json, xclbin and host app
  - build docker image (based on Dockerfile)
  - push this image in https://hub.docker.com Accelize repository account (https://cloud.docker.com/u/accelize/repository/list)
  - create a new Nimbix app: PushToCompute part
  - set git and docker repo variables
  - launch "Build+pull" for the App
  - the App is available on App list
  
## TODO:
  - move git repository to AWScodecommit
  - set ssh fetch key to allow 
  - define webhook to automate app update when modification ong git
  - set the contents of the app for demo propose (xclbin, host app, readme for documentation)



# Nimbix App creation documentation
Nimbix documentation for the full flow: https://jarvice.readthedocs.io/en/latest/cicd/

## Appdef documentation
more information on https://jarvice.readthedocs.io/en/latest/appdef/

## how to insert logo 
Command to insert Accelize logo: cat image/accelize_logo.png | base64 -w0 
apply the output result of the command on => "data" field in ApDef.json for logo insertion


# notes:


## build docker image from Dockerfile
docker build \
   --build-arg \
   DSA=xilinx_u200_xdma_201820_1 \
   --build-arg JARVICE_MACHINE=nx5u \
   --build-arg XCLBIN_PROGRAM=binary_container_1.xclbin \
   --build-arg XCLBIN_REMOVE=  \
   --file ./Dockerfile \
   -t accelize/repo:latest .
   
   
## push image on docker repository   
docker push accelize/repo:latest
(test with "accelize" account on "repo" repository on https://hub.docker.com)