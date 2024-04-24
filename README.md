1.1 # Version Control
Created a directory "MarketPeak_Ecommerce" and initialized a git repository inside the directory to manage the version control.
#Command to cretae directory and initialize
  ```bash
mkdir MarketPeak_Ecommerce
cd MarketPeak_Ecommerce
git init
```

1.2 #Download and prepare E-commerce template
Downloaded the Ecommerce template from this site: https://www.tooplate.com/view/2130-waso-strategy
Extract the folder into the "MarketPeak_Ecommerce folder created above.
Did some little customization on the template like changing the title, display text on the welcome page to suit my E-commerce website.

1.3 #Staged and Commit Template to Git
I staged the template and customizations to git using the "git.add ." command.
I set up some configurations on git to enable me track my changes using the "git config --global" command.
      git config --global user.name "[myUserName]"
      git config --global user.email "[myEmail]"

     Run: git commit -m "Intial commit ecommerce structure" command to commit the staged changes to Git.
I created a remote repository "MarketPeak_Ecommerce" on GitHub and Linked the local repository to it using this command:
  git remote add origin 
