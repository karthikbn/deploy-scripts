README.md for the Technical assignment

Topic : Containerise the given Vue.js app and build it from Jenkins & Deploy it on any given VM using Ansible

Tools used or required :

1) Jenkins hosted on any platform (Have used Linux Platform in my example)
  - Hostname : 13.82.18.164
  - Jenkins URL : http://13.82.18.164:8080
  - Test Username : deployer
  - Test Password : Welcome1 (Please note that admin access hasn't been granted for security reasons)

2) Deploy Node : Linux VM where the docker image will be deployed & containerised
  - Hostname : 40.117.177.67

3) Deployment Related Softwares :
      Latest version of Ansbile Installed on Jenkins Machine

4) Build Related Softwares :
      Latest version of npm & node js

5) Container Registry to store the docker images (Have used Azure CR here)




Replicating the Build & Deployment of Application

Build Procedure :

1) Code & Build Related Files are stored here :
    - https://github.com/karthikbn/my-first-app/tree/development

2) Build will be performed using Jenkinsfile via below Multi Branch Pipeline Jenkins Job
    - http://13.82.18.164:8080/job/my-first-app/job/development/
    - This generates a build using nom & then combines js and css for all the individual folders to convert them into one big minified, optimized  file and dockerize the same.
    - The build docker image will be tagged based on branch names (this has been pre-configured in the Jenkinsfile)
    - The new/updated image will then be pushed to the Container Registry

Deployment Procedure :
1) Deployment has been automated using Jenkins and ansible

2) All the required files are stored here :
    - https://github.com/karthikbn/deploy-scripts

3) All the required steps to automate the deployment are configured in the playbook
    - https://github.com/karthikbn/deploy-scripts/blob/master/docker_playbook.yml

4) The node details where the image has to be deployed are to be mentioned here
    - https://github.com/karthikbn/deploy-scripts/blob/master/hosts

5) Jenkins deploy Job
    - Below job will be used to deploy the docker image on the required hosts using Ansible as Configuration Management Tool
    - http://13.82.18.164:8080/job/deploy-app/

6) Once the deploy job is completed successfully - you can access the application via http://40.117.177.67:80
