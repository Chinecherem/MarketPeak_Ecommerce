# 1.1 Version Control
- Created a directory "MarketPeak_Ecommerce" and initialized a git repository inside the directory to manage the version control.
To cretae directory and initialize directory:
  ```bash
mkdir MarketPeak_Ecommerce
cd MarketPeak_Ecommerce
git init
```

# 1.2 Download and prepare E-commerce template
- Downloaded the Ecommerce template from this site: https://www.tooplate.com/view/2130-waso-strategy.
- Extracted the folder into the "MarketPeak_Ecommerce folder created above.
- Did some little customization on the template like changing the title, display text on the welcome page to suit my E-commerce website.

# 1.3 Staged and Commit Template to Git
I staged the template and customizations to git using the "git.add ." command.
I set up some configurations on git to enable me track my changes using the "git config --global" command.
      git config --global user.name "[myUserName]"
      git config --global user.email "[myEmail]"

     Ran: git commit -m "Intial commit ecommerce structure" command to commit the staged changes to Git.
- Created a remote repository "MarketPeak_Ecommerce" on GitHub and Linked the local repository to it using this command:
  git remote add origin https://github.com/Chinecherem/MarketPeak_Ecommerce.git.

I pushed the code to github main branch using "git push -u origin main" command.

# 2.1. Set Up an AWS EC2 Instance
I logged into the AWS Management Console and lunched an Amazon Linux AMI. 
Connected to the instance on my terminal and cloned the repository on the Linux server using SSH.

On my EC2 instance, I generated the ssh key using:
  ssh-keygen
Accessed the generated public key using: 
    cat /home/ubuntu/.ssh/id_rsa.pub  #display and copy the generated key from this directed

- Went back to github account, under setting, selected "SSH and GPS keys. 
Clicked on new SSH key, entered a name and pasted the SSH public key I copied above.

git clone git@github.com:Chinecherem/MarketPeak_Ecommerce.git: To clone the repository.

# Install a webserver on EC2

- Installed Apache2 web server on the EC2 instance using the below command
    sudo apt update
    sudo apt install apeche2
When the installation was completed, I cd into the default folder created by apeche; /var/www/html
Check the status of the apache web server using "sudo service apache2 status" command. This is to ensure if the server started automatically.
If the server didn't show an active flag, I will run "sudo service apache2 start" to start the server.

# Configured apache for website.
- Did an ls in the default folder shows the index.html file that contains the Apache2 default page.
- Cleared the contents of the default /var/www/html folder and copy the "MarketPeak_Ecommerce" website into it.
      sudo rm -rf /var/www/html/*
      sudo cp -r ~/MarketPeak_Ecommerce/*  /var/www/html/

- Applied the changes by reloading the apache2 service
    sudo service reload apache2

# Access Website from the browser.
-Copied the public IP on the EC2 instance to view the deployed website.

For continuous Integration and Development workflow, develop new Features and Fixes.
- Create a development branch from the main branch to isolate new features and bug fixes from the stable version of the website.
        git branch development
        git checkout developement : To swicth to the development branch
- Made changes and staged them using the "git add ." command.
- Commit the changes using: git commit -m "Added new feature"
- Pushed the changes to github using: git push origin development
- For code review and monitoring purpose, created a PR to merge the development branch into the main branch.
      git checkout main
      git merge development
      git push origin main: To push the changes to main.
  Also, can merge the developmet into the remote main branch on Github then on the local terminal;
        git checkout main
        git pull origin main: To merge the changes into the local repository.

- Restarted the apache server to apply the changes.
    sudo service reload apache2
  
- Accessed the webserver on the broswer to view my changes.

# CHALLENGES FACED
1. I wasn't clear what the Linux AMI(Amazon Machine Image) instance means so I created the instance wrongly by selecting the Linux AMI server on the quick start menu for creating instance on AWS management console. I realized the error when I ran the git clone command and got an error.I had to do a google search to understand how to create a Linux AMI instance.
2. My system wasn't using a yum package manager so the command to install httpd didn't work for me. Again, I browsed the problem and found a way to install the apache2 webserver using the "apt" command.
3. The changes I made on the website for the development branch to add feaures and bug fixes didn't reflect when I restarted the web server.  
    
