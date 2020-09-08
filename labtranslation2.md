Google Cloud Fundamentals: Getting Started with GKE

Objectives
In this lab, you learn how to perform the following tasks:

Provision a Kubernetes cluster using Kubernetes Engine.

Deploy and manage Docker containers using kubectl.

1.In GCP console, on the top right toolbar, click the Open Cloud Shell button.

2.For convenience, place the zone that Qwiklabs assigned you to into an environment variable called MY_ZONE. At the Cloud 

    export MY_ZONE=
followed by the zone that Qwiklabs assigned to you. Your complete command will look similar to this:

  export MY_ZONE=us-central1-a

3.Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes:

  gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2

It takes several minutes to create a cluster as Kubernetes Engine provisions virtual machines for you.

4.After the cluster is created, check your installed version of Kubernetes using the kubectl version command:

    kubectl version

5.Your Kubernetes cluster is now ready for use.

6.From your Cloud Shell prompt, launch a single instance of the nginx container.

  kubectl create deploy nginx --image=nginx:1.17.10

7.View the pod running the nginx container:

    kubectl get pods

8.Expose the nginx container to the Internet:

    kubectl expose deployment nginx --port 80 --type LoadBalancer

Kubernetes created a service and an external load balancer with a public IP address attached to it. The IP address remains the same for the life of the service. Any network traffic to that public IP address is routed to pods behind the service: in this case, the nginx pod.



9.View the new service:

    kubectl get services

  It may take a few seconds before the External-IP field is populated for your service. This is normal. Just re-run the kubectl get services command every few seconds until the field is populated.

10.Open a new web browser tab and paste your cluster's external IP address into the address bar. The default home page of the Nginx browser is displayed.

11.Scale up the number of pods running on your service:

  kubectl scale deployment nginx --replicas 3

  Scaling up a deployment is useful when you want to increase available resources for an application that is becoming more popular.


12.Confirm that Kubernetes has updated the number of pods:

    kubectl get pods

13.Confirm that your external IP address has not changed:

    kubectl get services
