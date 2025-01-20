# Bastion-Host-Project

This repository contains my hands-on snapshots of Bastion host process.

Procedure for Setting Up VPC with Public and Private Subnets

**Create a Virtual Private Cloud (VPC):**

* Define the VPC's CIDR block (e.g., 10.0.0.0/16).

**Create Public and Private Subnets:**

* Public Subnet:
   * Define a CIDR block within the VPC's range (e.g., 10.0.0.0/24).
* Private Subnet:
   * Define a CIDR block within the VPC's range (e.g., 10.0.1.0/24).

**Launch a Public EC2 Instance:**

* Select an appropriate Amazon Machine Image (AMI).
* Choose the public subnet.
* Enable "Auto-assign Public IP" in the network settings.

**Create and Attach an Internet Gateway:**

* Create an Internet Gateway.
* Attach the Internet Gateway to the created VPC.

**Create a Route Table:**

* Create a new Route Table within the VPC.

**Edit Route Table:**

* Add a route to the table:
* Destination: 0.0.0.0/0 (for all internet traffic)
* Target: The attached Internet Gateway.

**Associate Subnet with Route Table:**

* Associate the created Route Table with the public subnet.

**Launch a Private EC2 Instance:**

* Select an appropriate AMI.
* Choose the private subnet.
* Disable "Auto-assign Public IP" in the network settings.

**Connect to the Public Instance**:

* Use an SSH client (e.g., PuTTY, Terminal) and connect to the public instance using its public IP address and the appropriate credentials.

**Create and Secure the Key Pair File:**

* On the public instance, use the vi editor to create a new file (e.g., prasad.pem).
* Paste the contents of your key pair file into this new file.
* Save and exit the editor.

**Restrict permissions on the file:**

* chmod 400 prasad.pem

**Connect to the Private Instance:**

* Use the following SSH command to connect to the private instance:
* ssh -i prasad.pem ec2-user@<private_instance_private_ip>
* Replace <private_instance_private_ip> with the private IP address of the private instance.
