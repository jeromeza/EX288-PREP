# EX288 - Exam preparation

### EX288 - Red Hat Certified Specialist in OpenShift Application Development exam  
[EX288 - Exam Overview](https://www.redhat.com/en/services/training/ex288-red-hat-certified-specialist-openshift-application-development-exam?section=Overview)  
[EX288 - Exam Objectives](https://www.redhat.com/en/services/training/ex288-red-hat-certified-specialist-openshift-application-development-exam?section=Objectives)
  
### Version:  
EX288V46k  

### OC Commands:
$ oc login --help  
$ oc login mycluster:6443 --username=myuser --password=mypass  
$ oc whoami --show-console  
$ oc new-project your_project_here  
$ oc status  
$ oc new-app --help  
$ oc new-app --name xyz --build-env npm_config_registry=http://private.registry.com/nodejs http://mygit.com/xyz.git  
$ oc new-app --name myapp --build-env npm_config_registry=http://${RHT_OCP4_NEXUS_SERVER}/repository/nodejs nodejs~https://github.com/${RHT_OCP4_GITHUB_USER}/DO288-apps#app-config --context-dir app-config  

$ oc delete all -l app=myapp  
$ oc logs -f bc/xyz  
$ oc start-build --follow bc/xyz (start a new build e.g. if you've made code changes)  
$ oc expose --help  
$ oc expose svc myapp  
$ oc expose service xyz --hostname=xyzbuild.apps.cluster.domain.example.com  
$ oc get route 
$ oc create -f ~/your_template.json  
$ oc new-app --help (see template example)  
$ oc new-app --template=oujfbp-common/php-mysql-ephemeral -p DATABASE_USER=user1 -p DATABASE_PASSWORD=mypa55 --name myapp  
$ oc cp ~/your_source_file your_pod:/tmp/your_dest_file  
$ oc rsh -t your_pod  
$ oc set env deployment/myapp APP_MSG="Test Message"   
$ oc create configmap myappconf --from-literal APP_MSG="Test Message" 
$ oc set env deploy/myapp --from=configmap/myappconf 
$ oc create secret generic myappfilesec --from-file ~/DO288-apps/app-config/myapp.sec  
$ oc set volume deployment/myapp --add -t secret --name=myappsec-vol --secret-name myappfilesec --mount-path=/opt/app-root/secure/  
  
### PODMAN COMMANDS:
$ podman build -t do288-hello-java ~/DO288-apps/hello-java/ --format=docker  
$ podman tag do288-hello-java quay.io/${RHT_OCP4_QUAY_USER}/do288-hello-java  
$ podman login quay.io -u ${RHT_OCP4_QUAY_USER}  
$ podman push quay.io/${RHT_OCP4_QUAY_USER}/do288-hello-java  

### VALIDATE JSON:
$ python3 -m json.tool my.json

### GIT Commands:
$ git clone https://github.com/myrepo.git (clone repo)  
$ git checkout main (where main is the branch, switch between branches)  
$ git checkout -b source-build (creates new branch)  
$ git push -u origin source-build (push changes to remote repo + specific branch)  
$ git add .  
$ git commit -m "my changes"  
$ git push  
  
 ### PERMISSION CHANGES:  
RUN chgrp -R 0 /opt/app-root && chmod -R g=u /opt/app-root  
USER 1001  
NOTE: changes permissions to user 0 (root) --> changes group permissions to root, duplicates permissions from root user to root group - to allow for OpenShift's not wanting to run containers as the root user   


