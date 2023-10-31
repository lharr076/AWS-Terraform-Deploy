  <h1><b>Deploying a Cyber security homelab using Terraform</b></h1>
  <p>Welcome to the blog of <span class="w3-tag">Larry Harris Jr</span></p>


  <img src="/images/automation1.png" alt="Automation" style="width:25%">
    <h3><b>Deploying a Cyber security homelab using Terraform</b></h3>
    <h5>Date, <span class="w3-opacity">October 7-8, 2023</span></h5>
  
    <p>Resources used:</p>
    <ul class="resources">
      <li><a href="https://youtu.be/2cMkpLoKUj0?si=AfstrUg3wtZGRXFb">Build a Cloud Red Team / Blue Team Cybersecurity Homelab - Crash Course</a></li>
      <li><a href="https://developer.hashicorp.com/terraform/downloads">Terraform Install</a></li>
      <li><a href="https://learn.microsoft.com/en-us/windows/wsl/install">WSL Install</a></p></li>
    </ul>  

    
      <img src="images/WSL Install.png" alt="WSL Install" style="width: 100%">
      <p>Step1: Install WSL: Open Powershell and type in command "wsl --install" to install the Windows Subsystem for Linux.
        I already have WSL installed so we proceed on to the next step. </p></br>
      
        <img src="images/git clone .png" alt="Git Install and Clone" style="width: 100%">
      
      <img src="images/terraform main_tf file.png" alt="Terraform File Location" style="width: 100%">
        
       <p>Step2:If you do not have Git, you will need to install it in order to download from Github.
        The command to install Git is, <span style="color: green;">sudo apt install git</span> After I installed Git,
         insert command, <span style="color: green;">git clone https://github.com/collinsmc23/cloud-cybersecurity-homelab.git</span>.
        Afterwards I changed directories into the folder I downloaded.
      </p>
       <img src="images/kali ami modify.png" alt="Highlighted AMI" style="width: 100%">
        <p>Step3: As you locate the two comments that state "Create Windows" or "Create Kali Instance", look two lines down and you will see the 
          AMI ID. In my case I need to change the AMI ID  with what was avail currently on AWS. In order to do this, just get on AWS and 
          choose your prefered AMIs for your machines.
        </p></br>
      <img src="images/install terraform.png" alt="Terraform Install" style="width: 100%">
        <p>Step4: Install Terraform using the command, <span style="color: green;">wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
          echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
          sudo apt update && sudo apt install terraform</span></p></br>
      <div class=" w3-container w3-cell">
        <img src="images/Create IAM user1.png" alt="IAM user1" style="width: 100%">
      </div>
        <div class=" w3-container w3-cell">
          <img src="images/Create IAM user2.png" alt="IAM user2" style="width: 100%">
       </div>
        <p>Step5: Create IAM User to use access AWS through Terraform. Creating the IAM user in AWS is straight forward. After you have 
          created a user, This user needs full EC2 and VPC access in order for Terraform to perform its actions. What you will need to save for 
          later is the access key ID and private key. When you are setting up the IAM user, you will have the chance to save the secret key to store in 
          in a safe place for later and you will need the access key ID also to input into the credential file later on.
        </p></br> 
      <img src="images/nano credential file create.png" alt="Nano File credential" style="width: 100%">
        <p>Step6: Create NANO credentials file if one by default is not created. If a default Nano file was not created, you can create one by 
          simply typing <span style="color: green;">nano credentials</span> in the command line and you will be able to create the file. 
          Although not displayed, at the top, you would want "default" displayed as such, <span style="color: green;">[default]</span> within Nano,
          insert <span style="color: green;">aws_access_key_id =</span> (insert new IAM user access id). Go to next line and insert 
          <span style="color: green;">aws_secret_access_key=</span> (insert your secret key that you have saved in a safe location).
          To save any updated information, you will press CTRL X, Y, then press Enter.
        </p></br>
      
      <img src="images/terraform initialize .png" alt="Terraform initialize" style="width: 100%">
        <p>Step7: "terraform initialize" installs the plugin for AWS.</p></br>
      <div class=" w3-container w3-cell">
        <img src="images/terraform plan1.png" alt="Terraform plan1" style="width: 100%">
      </div>
      <div class=" w3-container w3-cell">
        <img src="images/terraform plan8.png" alt="Terraform plan8" style="width: 100%">
      </div>
        <p>Step8: Here the "terraform plan" command is being ran. Here Terraform will run the code</p></br>
      <div class=" w3-container w3-cell">
        <img src="images/terraform apply error.png" alt="Terraform plan1" style="width: 100%">
      </div>
      <div class=" w3-container w3-cell">
        <img src="images/terraform apply successful.png" alt="Terraform plan8" style="width: 100%">
      </div>
        <p>Step9: In this section I display an issue that I ran into while running the Terraform code. 
          I am showing what will appear if you do not go into the Terraform "main.tf" file and modify the AMI ID of instances you are intending on running.
        Once I changed the AMI IDs, as you see in the right image, the command ran with no issue.</main></p></br>
      <img src="images/homelab in cloud.png" alt="Lab in Cloud" style="width: 100%">
        <p>Step10: The Cybersecurity homelab set up in the cloud.</p></br>
      <img src="images/terraform destroy.png" alt="Terraform Destroy" style="width: 100%">
        <p>Step11: The "terraform destroy" command after completion.</p></br>
      <img src="images/homelab teardown.png" alt="Lab Teardown" style="width: 100%">  
        <p>Step12: As you can see here, all three machines have been terminated to help keep your cost down.</p>
      <div class="w3-col m4 w3-hide-small">
        <p><span class="w3-padding-large w3-right"><b></b> <span class="w3-tag"></span></span></p>

