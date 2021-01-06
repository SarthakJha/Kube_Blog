# Kube_Blog
This is a basic blogging application built on **Microservice** architecture. Entire backend is written in **NodeJS** and **express** and basic front-end client is written in **React**.
 The entire application is brought to life using **Kubernetes** and **Docker**.

 **Microservices inside the cluster are:-**
 1. **Client**(Docker image: *sarthakjha/client*)
  : Front-end React client


 2. **Comments**(Docker image: *sarthakjha/comments*): Handles comments of a blog
 3. **Event-bus**(Docker image: *sarthakjha/event-bus*): (basic impl. of a message queue) Handles transportation of data within the cluster
 4. **Moderation**(Docker image: *sarthakjha/moderation*): Reviews the submitted comments for certain words. If some specific word is present it deletes the comment with *This comment has been rejected*. (In this application, the trigger word is *orange* xD)
 5. **Posts**(Docker image: *sarthakjha/posts*): manages the posting of blogs
 6. **Query**(Docker image: *sarthakjha/query*): manages queries

**Dedicated db have not been used for persistance bcos its a basic application. It uses in memory storage instead**

  *Make sure you have docker and kubernetes installed and running*
  
  We will be using skaffold to deploy all the services and deployments. Download from [here](https://skaffold.dev/docs/install/)
  
and finally follow the [steps](https://kubernetes.github.io/ingress-nginx/deploy/#docker-for-mac) to run an ingress-nginx pod for internal cluster routing depending on your OS

To check if the nginx pod is running successfully, run 
`kubectl get ns` and see if **ingress-nginx** is there.

  
  
  To check if the required softwares are downloaded, run the following on the terminal:
 - `docker --version` 
 - `kubectl version`
 - `skaffold version`
 
 
 **Follow the steps to start kubernetes cluster locally:-**
 1. Clone the repository change into the cloned directory on the terminal
 2. run `skaffold dev`

 lastly to run the client, edit the */etc/hosts* file and add **127.0.0.1 posts.com** in that file.
 
 A bunch of output will be visible on the terminal regarding the status of the applications in the cluster. If there are any errors, run the following commands to debug 
 1. `kubectl get pods`
 2. `kubectl get services`
 3. `kubectl get deployments`
 
 The above commands will give the status of the applications in the cluster
 which can be used to debug the errors.
 
 



