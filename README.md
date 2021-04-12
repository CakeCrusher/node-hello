# Node Hello World.. with pm2 on an AWS ec2 instance.
Node.js with pm2 (a process manager to help you manage your app online) app for an ec2 environment.

The following guide can help you get started building a AWS Node virtual machine with the powerful process management system pm2.

## Guide from ssh connection to deployed app.

This guide will take you step by step on how to deploy a node server with the process manager pm2 on an AWS ec2 virtual machine.

1. Make an ssh connection to your aws instance
2. Download Node Version Manager (nvm) with:  `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash`
3. Activate nvm with: `. ~/.nvm/nvm.sh`
4. Install Node with: `nvm install node`
5. Download git with: `sudo yum install git`
6. Clone this simple node hello world server https://github.com/johnpapa/node-hello with `git clone https://github.com/johnpapa/node-hello.git`
7. Navigate to the node-hello directory with: `cd node-hello/`
8. Install pm2 with: `npm install -g pm2@3.2.2` (the latest version results in unresolved errors)
9. Create a startup script with: `pm2 start index.js` (index.js is the file to run the server in this repository)
10. Create a generate an ecosystem configuration file with: `pm2 ecosystem`
11. Ensure that the script is index.js with: `cat ecosystem.config.js` ![image](https://user-images.githubusercontent.com/37946988/114453347-0d4a2380-9b9f-11eb-9618-dc28b7931028.png)
12. If it does continue. Otherwise refer to this page for information on how to edit the file so that the script leads to index.js: https://www.howtoforge.com/faq/how-to-edit-files-on-the-command-line.
13. Finally run the server with ec2: `pm2 reload ecosystem.config.js --env production`
14. Find your instance's public ip address: ![image](https://user-images.githubusercontent.com/37946988/114454213-f821c480-9b9f-11eb-8858-19ab55021c04.png)
15. Add Inbound Rules: head to your aws dashboard -> find and click on 'Security' -> Click on the 'Security groups' url -> click on 'Edit inbound rules' -> create the following rule: ![image](https://user-images.githubusercontent.com/37946988/114455384-51d6be80-9ba1-11eb-8cc2-79a58ba11805.png) -> click on 'Save rules'
16. Navigate to: http://YOUR_INSTANCE_PUBLIC_IP_ADDRESS:3000/
17. Congratulations!


`npm start`
