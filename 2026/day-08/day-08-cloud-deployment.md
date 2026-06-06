# Day 08 – Cloud Deployment

## Commands Used

sudo apt update  
sudo apt install docker.io -y  
sudo systemctl start docker  
sudo apt install nginx -y  
sudo systemctl start nginx  
sudo systemctl enable nginx  
sudo journalctl -u nginx -n 50 > nginx-logs.txt  

## Challenges Faced

Initially faced issues with accessing nginx due to networking and security group configuration.  
Solved by correctly setting security group rules and using Elastic IP.

## What I Learned

- How to launch and connect to a cloud server  
- How to install and manage services using systemctl  
- Importance of security groups and networking in AWS  
- How to view and extract logs using journalctl  
- Real-world troubleshooting approach  

## Why This Matters for DevOps

This task helped me understand real-world server setup, deployment, and debugging.  
These skills are essential for managing production systems.


 ssh -i linux-for-devops-key.pem ubuntu@ec2-52-44-100-225.compute-1.amazonaws.com  // extablished ssh connection between local and ec2 server, for this local must have private key which was there in downloads and server has the public key


The authenticity of host 'ec2-52-44-100-225.compute-1.amazonaws.com (52.44.100.225)' can't be established.
ED25519 key fingerprint is SHA256:caOi05oNCGQ5dMidwIQJD2DK3DkUM53jTAz3rTMjgAE.
This host key is known by the following other names/addresses:
    C:\Users\Desktop/.ssh/known_hosts:1: ec2-44-213-116-138.compute-1.amazonaws.com
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'ec2-52-44-100-225.compute-1.amazonaws.com' (ED25519) to the list of known hosts.
Welcome to Ubuntu 24.04.3 LTS (GNU/Linux 6.17.0-1009-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Wed Mar 25 11:01:46 UTC 2026

  System load:  0.0               Temperature:           -273.1 C
  Usage of /:   37.8% of 6.71GB   Processes:             116
  Memory usage: 24%               Users logged in:       0
  Swap usage:   0%                IPv4 address for ens5: 172.31.0.235

 * Ubuntu Pro delivers the most comprehensive open source security and
   compliance features.

   https://ubuntu.com/aws/pro

Expanded Security Maintenance for Applications is not enabled.

41 updates can be applied immediately.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


Last login: Tue Mar 24 08:16:10 2026 from 103.133.65.135
ubuntu@ip-172-31-0-235:~$
