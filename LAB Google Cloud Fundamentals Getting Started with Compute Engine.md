# LAB: Google Cloud Fundamentals: Getting Started with Compute Engine



## Objectives

In this lab, you will learn how to perform the following tasks:

- Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.
- Create a Compute Engine virtual machine using the gcloud command-line interface.
- Connect between the two instances.



## Task 1: Create a virtual machine using the GCP Console

gcloud compute instances create \
diramy-vm-1 --zone=europe-west2-a --machine-type=n1-standard-2 \
--image-project=debian-cloud --image=debian-a-stretch-v20190213 \
--subnets=default --tags=http



## Task 2: Create a virtual machine using the gcloud command line



### To display a list of all the zones in the region

gcloud compute zones list | grep us-central1



### To set your default zone to the one you just chose, enter this partial command gcloud config set compute/zone followed by the zone you chose.

gcloud config set compute/zone us-central1-b



### To create a VM instance called my-vm-2

gcloud compute instances create "my-vm-2" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image "debian-9-stretch-v20190213" \	
--subnet "default"



### To close the Cloud Shell

exit



## Task 3: Connect between VM instances



### To connect to my-vm-2 SSH

gcloud compute ssh my-vm-2



### Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network:

ping my-vm-1



-Press Ctrl+C to abort the ping command.



### Use the ssh command to open a command prompt on my-vm-1:

ssh my-vm-1



-If you are prompted about whether you want to continue connecting to a host with unknown authenticity, enter yes to confirm that you do.



### At the command prompt on my-vm-1, install the Nginx web server

sudo apt-get install nginx-light -y



### Use the nano text editor to add a custom message to the home page of the web server

sudo nano /var/www/html/index.nginx-debian.html



### Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name

Hi from YOUR_NAME



-Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor



### Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command

curl http://localhost/



### To exit the command prompt on my-vm-1

exit



### To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2,

curl http://my-vm-1/