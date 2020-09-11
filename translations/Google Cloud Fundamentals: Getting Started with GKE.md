# Lab: App Dev: Setting up a Development Environment v1.1 

## Objectives

In this lab, you will learn how to perform the following tasks:

   - Provision a Google Compute Engine instance.

   - Connect to the instance using SSH.

   - Install software on the instance.

   - Verify the software installation.

## Steps
1. Creating a Compute Engine Virtual Machine Instance
    >`gcloud beta compute --project=qwiklabs-gcp-03-751c773f90b1 instances create dev-instance --zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM --maintenance-policy=MIGRATE --service-account=466896154539-compute@developer.gserviceaccount.com --scopes=https://www.googleapis.com/auth/cloud-platform --tags=http-server --image=debian-10-buster-v20200902 --image-project=debian-cloud --boot-disk-size=10GB --boot-disk-type=pd-standard --boot-disk-device-name=dev-instance --no-shielded-secure-boot --no-shielded-vtpm --no-shielded-integrity-monitoring --reservation-affinity=any
    `  

    >`gcloud compute --project=qwiklabs-gcp-03-751c773f90b1 firewall-rules create default-allow-http --direction=INGRESS --priority=1000 --network=default --action=ALLOW --rules=tcp:80 --source-ranges=0.0.0.0/0 --target-tags=http-server
    `
    <br>

   
2. Install software on the VM instance
   1. In the SSH session, to update the Debian package list, execute the following command:  
    `sudo apt-get update`
   2. To install Git, execute the following command:  
    `sudo apt-get install git`
         If prompted, press Enter.
   3. To download the Node.js setup script, execute the following command:  
    `curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -`
   4. To install npm and Node.js, execute the following command:  
    `sudo apt install nodejs`

   
3. Configure the VM to Run Application Software
    1. To check the version of Node.js, execute the following command:  
     `node -v`
    2. To clone the class repository, execute the following command:  
     `git clone https://github.com/GoogleCloudPlatform/training-data-analyst`
    3. To change the working directory, execute the following command:  
     `cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/`
    4. To run a simple web server, execute the following command:  
     `sudo node server/app.js`
    5. In the VM instance list, choose the external IP address for the dev instance.
        `gcloud compute instances list`
        `gcloud compute instances describe my-instance --format='get(networkInterfaces[0].accessConfigs[0].natIP)'`  
        >Then put the link in your browser like this ``http://<IP-EXTERNAL-VM>``
        
        >You should see a Hello GCP dev! message from Node.js.

    6. Return to the SSH window, and stop the application by pressing Ctrl+C.  
    7. To install the Node.js library for Compute Engine, execute the following command:  
     `npm install`
    8. To run a simple Node.js application that lists Compute Engine instances, execute the following command:  
     `node list-gce-instances.js`
