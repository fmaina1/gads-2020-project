
Google Cloud Fundamentals: Getting Started with Compute Engine

Objectives
In this lab, you will learn how to perform the following tasks:

Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

Create a Compute Engine virtual machine using the gcloud command-line interface.

Connect between the two instances.


1.In GCP console, on the top right toolbar, click the Open Cloud Shell button.

2.Click Continue

To display a list of all the zones in the region to which Qwiklabs assigned you, enter this partial command

  gcloud compute zones list | grep us-central1

3.To set your default zone to the one you just chose

  gcloud config set compute/zone us-central1-b

4 create a VM instance called my-vm-2 

    gcloud compute instances create "my-vm-2" \
  --machine-type "n1-standard-1" \
  --image-project "debian-cloud" \
  --image "debian-9-stretch-v20190213" \
  --subnet "default"

Should take about 2 Minutes for the VM to launch


Connect between the two instances.

1. Navigate via the Menu Select Compute Engine> VM instances

2.To open a command prompt on the my-vm-2 instance, click SSH in its row in the VM instances list.

3. Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network:

    ping my-vm-1
4.Ctr+C to abort ping command

5.Use the ssh command to open a command prompt on my-vm-1

  ssh my-vm-1
