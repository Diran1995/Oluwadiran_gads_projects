# LAB:Creating Virtual Machines



## Objectives

In this lab, you explore the available options for VMs and see the differences between locations.
In this lab, you learn how to perform the following tasks:

- Create several standard VMs
- Create advanced VMs



## Task 1: Create a utility virtual machine
	gcloud compute instances create diranvm --zone=us-central1-c --machine-type=n1-standard-1



## Task 2: Create a Windows virtual machine

gcloud compute instances create \
diranvm-eu --zone=europe-west2-a --machine-type=n1-standard-2 \
--image-project=windows-cloud --image=windows-server-2016-dc-core-v20200813 \
--boot-disk-type=pd-ssd --boot-disk-size=100GB \
--tags=http --tags=https



### Connect to the windows desktop

#### Set the password

	gcloud compute reset-windows-password diranvm-eu --zone=europe-west2-a

then click y and enter
and click y and enter



## Task 3: Create a custom virtual machine

	gcloud compute instances create diran-us --zone=us-west1-b --custom-cpu=6 --custom-memory=32



### Connect to diran-us SSH

gcloud compute ssh diran-us



### To see details about RAM installaled on your VM

	sudo dmidecode -t 17



### To verify number of processors

	nproc



### To sec details about the cpu installed on your vm

	lsc.pu



### To exit the SSH terminal

	`exit`