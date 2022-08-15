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
$ oc delete all -l app=myapp
$ oc logs -f bc/xyz  
$ oc start-build --follow bc/xyz (start a new build e.g. if you've made code changes)  
$ oc expose --help  
$ oc expose service xyz --hostname=xyzbuild.apps.cluster.domain.example.com  
$ oc get route 

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
