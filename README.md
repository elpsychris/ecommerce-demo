# E-commerce Demo

This is a sample application that demonstrates an E-commerce website using the MEAN stack. The application loads 
products a MongoDB database and displays them. Users can select to display products in a single category. Users can 
click on any product to get more information including pricing, reviews and rating. Users can select items and 
add them to their shopping cart

## Import Data
I have included a data folder in this repo. Inside that folder will be 2 folders called cart and item. These 2 folders contain a mongodump of the 2 collections that I use in this ecommerce demo. You can use the [import-data.sh](data/import-data.sh) script to import these 2 dumps to an ecommerce database, then you will have the same content that I have for this demo.

## Getting Started
To get started  you can simply clone this `ecommerce-demo` repository and install the dependencies.

Clone the `ecommerce-demo` repository using git:

```bash
git clone https://github.com/ratracegrad/ecommerce-demo
cd ecommerce-demo
```

Install dependencies with this command:
```bash
npm install
```

If postscript did not work correctly (angular had not been installed), run this command mannually:
```bash
bower install
```

Run the application with this command:
```bash
npm start
```

## Tech Stack
* AngularJS
* Node.js
* Express.js
* Bootstrap
* ui-Router

## How to deploy this web on AWS VPC
Connect to your VPC through SSH (assured that your VPC instance is running and port 22 is opening in your Security Group)

### My VPC's information:

**Instance type**: EC2 t2.micro
**OS**: Ubuntu 18.04
**Virtualization**: hvm

### Network rules
**Inbound ports**: 22, 3000
**Outbound ports**: All


```bash
ssh -i ~/Downloads/mykey2.pem ubuntu@<VPC IP address>
```
Next, copy your project folder to the host's storage (I used Secure Copy for this task) and my project located in home directory in the VPC.

```bash
sudo scp -vr -i <path to pem file for VPC authentication> <path to project folder in your PC> ubuntu@<AWS VPC ip address>:~/
```

**ATTENTION:** ```DO NOT COPY THE *nodes_modules* folders (NODEJS DEPENDENCIES FROM *npm install*) IF YOU DO NOT WANT TO WAIT FOR TOO LONG```

Then, install MongoDB for the VPC and restore the data as the above instructions and done, you had the web run on your VPC

Remember to run the *npm install* command as a deamon process with

```bash
nohup sudo npm start &
```

If not, the server will be closed immediately the second you close the ssh connection




