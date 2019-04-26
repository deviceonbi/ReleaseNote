Command line instructions

Git global setup
git config --global user.name "xiaochen.shi"
git config --global user.email "xiaochen.shi@advantech.com.cn"

Create a new repository
git clone git@advgitlab.eastasia.cloudapp.azure.com:deviceon/WISEMPlusLog.git
cd WISEMPlusLog
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

Existing folder
cd existing_folder
git init
git remote add origin git@advgitlab.eastasia.cloudapp.azure.com:deviceon/WISEMPlusLog.git
git add .
git commit
git push -u origin master

Existing Git repository
cd existing_repo
git remote add origin git@advgitlab.eastasia.cloudapp.azure.com:deviceon/WISEMPlusLog.git
git push -u origin --all
git push -u origin --tags