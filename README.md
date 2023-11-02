 <h1>Deploying a Cyber security homelab using Terraform</h1> <br />
 <p align="center">
 This was my first time experiencing the power of Terraform and I really enjoyed doing this project. With this project, it help me see what's under the hood when it comes to IaC.
 <br />
 <br />
 <br />
 <p align="center">   
Launch the utility: Step1: Install WSL: Open Powershell and type in command "wsl --install" to install the Windows Subsystem for Linux. I already have WSL installed so we proceed on to the next step.  <br/>
<img src="https://i.imgur.com/5htnIkE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Git: Step2:If you do not have Git, you will need to install it in order to download from Github. The command to install Git is, sudo apt install git After I installed Git, insert command, git clone https://github.com/collinsmc23/cloud-cybersecurity-homelab.git. Afterwards I changed directories into the folder I downloaded.   <br/>
<img src="https://i.imgur.com/EVb9wbs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Modify terraform file: Step3: As you locate the two comments that state "Create Windows" or "Create Kali Instance", look two lines down and you will see the AMI ID. In my case I need to change the AMI ID with what was avail currently on AWS. In order to do this, just get on AWS and choose your prefered AMIs for your machines. <br/>
<img src="https://i.imgur.com/JkAwxHB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Install Terraform: Step4: Install Terraform using the command, wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list sudo apt update && sudo apt install terraform <br/>
<img src="https://i.imgur.com/Gtz7h68.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create IAM user: Step5: Create IAM User to use access AWS through Terraform. Creating the IAM user in AWS is straight forward. After you have created a user, This user needs full EC2 and VPC access in order for Terraform to perform its actions. What you will need to save for later is the access key ID and private key. When you are setting up the IAM user, you will have the chance to save the secret key to store in in a safe place for later and you will need the access key ID also to input into the credential file later on. <br/>

|                             |                             |
| ----------------------------------- | ----------------------------------- |
| ![IAM1](https://i.imgur.com/xZEFBnl.png) | ![IAM2](https://i.imgur.com/4Hk2HbL.png) |

<br />
<br />
Create NANO credentials file: Step6: Create NANO credentials file if one by default is not created. If a default Nano file was not created, you can create one by simply typing nano credentials in the command line and you will be able to create the file. Although not displayed, at the top, you would want "default" displayed as such, [default] within Nano, insert aws_access_key_id = (insert new IAM user access id). Go to next line and insert aws_secret_access_key= (insert your secret key that you have saved in a safe location). To save any updated information, you will press CTRL X, Y, then press Enter.  <br/>
<img src="https://i.imgur.com/5q2arnp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Initialize Terraform: Step7: "terraform initialize" installs the plugin for AWS. <br/>
<img src="https://i.imgur.com/FnHIr1f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Terraform Plan: Step8: Here the "terraform plan" command is being ran. Here Terraform will run the code. <br/>

|                             |                             |
| ----------------------------------- | ----------------------------------- |
| ![IAM1](https://i.imgur.com/cZ72l0R.png) | ![IAM2](https://i.imgur.com/oMfWjnc.png) |

<br />
<br />
Terraform Apply: Step9: In this section I display an issue that I ran into while running the Terraform code. I am showing what will appear if you do not go into the Terraform "main.tf" file and modify the AMI ID of instances you are intending on running. Once I changed the AMI IDs, as you see in the right image, the command ran with no issue. <br/>

|                             |                             |
| ----------------------------------- | ----------------------------------- |
| ![IAM1](https://i.imgur.com/n7JAALy.png) | ![IAM2](https://i.imgur.com/MrQIv6D.png) |

<br />
<br />
Step10: The Cybersecurity homelab set up in the cloud. <br/>
<img src="https://i.imgur.com/JHaCAs7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Terraform: Step11: The "terraform destroy" command after completion. <br/>
<img src="https://i.imgur.com/X8jSGD3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Step12: As you can see here, all three machines have been terminated to help keep your cost down. <br/>
<img src="https://i.imgur.com/NAWKUfX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

