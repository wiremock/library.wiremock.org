---
slug: "bluemix-net-containers"
title: "IBM Containers API"
provider: "bluemix.net"
description: "Containers are virtual software objects that include all the elements\
  \ that an app needs to run. A container has the benefits of resource isolation and\
  \ allocation but is more portable and efficient than, for example, a virtual machine.\n\
  \n This documentation describes the IBM Containers API, which is based on the Docker\
  \ Remote API. The API provides endpoints that you can use to create and manage your\
  \ single containers and container groups in Bluemix. Endpoints are summarized under\
  \ the following tags: \n\n- **Authentication**: Retrieve and refresh your TLS certificates.\
  \ \n- **Private Docker images registry**: Create your own private Docker images\
  \ registry in Bluemix by setting a namespace for your organization. \n- **Images**:\
  \ View, build, and push your images to your private Bluemix registry so you can\
  \ use them with IBM Containers. You can also scan your container images with the\
  \ Vulnerability Advisor against standard policies set by the organization manager\
  \ and a database of known Ubuntu issues. \n- **Single Containers**: Create and manage\
  \ single containers in Bluemix. Use a single container to implement short-lived\
  \ processes or to run simple tests as you develop an app or service. To make your\
  \ single container available from the internet, review the `Public IP addresses`\
  \ endpoints. \n- **Container Groups**: Create and manage your container groups in\
  \ Bluemix. A container group consists of multiple single containers that are all\
  \ created from the same container image and as a consequence are configured in the\
  \ same way. Container groups offer further options at no cost to make your app highly\
  \ available. These options include in-built load balancing, auto-recovery of unhealthy\
  \ container instances, and auto-scaling of container instances based on CPU and\
  \ memory usage. Map a public route to your container group to make your app accessible\
  \ from the internet.  \n- **Public IP addresses**: Use these endpoints to request\
  \ public IP addresses for your space. You can bind this IP address to your container\
  \ to make your container accessible from the internet. \n- **File shares**: Create,\
  \ list and delete file shares in a space. A file share is a NFS storage system that\
  \ hosts Docker volumes.  \n- **Volumes**: Create and manage container volumes in\
  \ your space to persist the data of your containers.  \n\n\n Each API request requires\
  \ an HTTP header that includes the 'X-Auth-Token’ and 'X-Auth-Project-Id’ parameter.\
  \ \n\n- **X-Auth-Token**: The JSON web token (JWT) that you receive when logging\
  \ into the Bluemix platform. It allows you to use the IBM Containers REST API, access\
  \ services, and resources. Run `cf oauth-token` to retrieve your access token information.\n\
  - **X-Auth-Project-Id**: The unique ID of your organization space where you want\
  \ to create or work with your containers. Run `cf space <space_name> --guid`, where\
  \ `<space_name>` is the name of your space, to retrieve your space ID.\n\n\n For\
  \ further information about how containers work in the IBM Containers service, review\
  \ the documentation under https://new-console.ng.bluemix.net/docs/containers/container_index.html. "
logo: "bluemix.net-containers-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "developer_tools"
stubs: "bluemix.net-containers-stubs.json"
swagger: "bluemix.net-containers-swagger.json"
---
