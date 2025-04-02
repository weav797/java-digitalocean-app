# Java DigitalOcean App Deployment

## Overview
This project demonstrates the process of deploying a Java Gradle application on a DigitalOcean Droplet. It is part of the **Techworld with Nana Bootcamp** under **Module 5: Cloud & Infrastructure as a Service Basics**.

## Technologies Used
- **Cloud Provider:** DigitalOcean
- **Operating System:** Linux (Ubuntu)
- **Programming Language:** Java
- **Build Tool:** Gradle

## Prerequisites
Before deploying the application, ensure you have the following:
- A **DigitalOcean account**
- SSH access configured on your local machine
- Basic knowledge of Linux commands
- Java installed on the Droplet

## Project Setup & Deployment
This section covers the step-by-step deployment process.

### 1. Create a DigitalOcean Droplet
The Droplet was created using the **DigitalOcean web interface**. The following configurations were applied:
- **Image:** Ubuntu 24.10
- **Size:** 1 vCPU, 512 MB RAM
- **Region:** San Francisco
- **Authentication:** SSH Key

### 2. Configure Firewall Rules
A firewall was set up with the following inbound rules:
- **Port 22 (SSH):** Allowed only from my IP address for secure access
- **Port 7071:** Open to all inbound traffic since the application listens on this port

### 3. Connect to the Droplet
```bash
ssh root@IP_ADDRESS_REDACTED
```

### 4. Create a New User and Configure SSH Access (Security Best Practice)
```bash

adduser paul

usermod -aG sudo paul

su - paul
```
Set up SSH key authentication for the new user:
```bash

mkdir -p ~/.ssh

sudo vim ~/.ssh/authorized_keys # Copy/paste the public SSH key

cat ~/.ssh/authorized_keys
```

### 5. Install Java
```bash
apt update && apt install -y openjdk-8-jre-headless
```

### 6. Deploy the Application
Since the application was built using Gradle on the local client machine, only the compiled JAR file needs to be transferred to the server. Use `scp` to copy the artifact:
```bash
scp build/libs/java-digitalocean-app.jar root@IP_ADDRESS_REDACTED:/root
```
SSH into the server and run the application:
```bash
java -jar java-digitalocean-app.jar
```

## Lessons Learned & Challenges
- Setting up a secure DigitalOcean instance
- Managing a Java Gradle project in a cloud environment

## Reference
- [DigitalOcean Documentation](https://docs.digitalocean.com)

---
This project is part of my bootcamp training and showcases my ability to deploy applications in a cloud environment.<br /><br /><br /><br />

More notes down below from the original source of the repo.

# Java-React Example

An example of how to use JS frontend to consume an endpoint written in Java.

## Frontend technologies

- [React](https://facebook.github.io/react/) - UI Library
- [Redux](http://redux.js.org/) - State container

## Additional information

This project is a part of a [presentation](https://docs.google.com/presentation/d/1-yZhsM43cyWWDVn6EUtK_wc39FAv-19_jwsKXlTe2o8/edit?usp=sharing)

Related projects:

- [react-intro](https://github.com/mendlik/react-intro) - Introduction to react and redux.
- [java-webpack-example](https://github.com/mendlik/java-webpack-example) - Advanced example showing how to use a module bundler in  a Java project.

Tip: [How to enable LiveReload in IntelliJ](http://stackoverflow.com/a/35895848/2284884)

<hr/>
Original project can be found here: https://github.com/pmendelski/java-react-example
