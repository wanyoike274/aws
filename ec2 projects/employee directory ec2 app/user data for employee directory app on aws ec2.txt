#!bin/bash -ex

#update yum
yum -y update

#add node's source repo
curl -sL https://rpm.nodesource.com/setup_15.x | bash -

#install nodejs
yum -y install nodejs

#create a dedicated directory for the application
mkdir -p /var/app

#get the app from s3
wget https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/ILT-TF-100-TECESS-5/app/app.zip

#unzip it into a specific folder
unzip app.zip -d /var/app/

cd /var/app/

#install dependencies
npm install

#start your app
npm start