# testFlask-Gitops
Sample Openshift-Gitops(ArgoCD) for a Flask Python Application<br/>

## Pre-Requisites:<br/> 
Install Openshift Pipelines Operator:https://docs.openshift.com/container-platform/4.6/pipelines/installing-pipelines.html<br/>
## Pre-Requisites:<br/>
Install Openshift GitOps Operator:https://docs.openshift.com/container-platform/4.7/cicd/gitops/understanding-openshift-gitops.html<br/>
## Pre-Requisites: <br/>
Install Sealed Secrets Operator: Manifest is Provided under the sealed secret environements, should get installed<br/>

## Pre-Requisites: <br/>
## You can install the pre-requisites via:<br/>
1 Install Openshift-Gitops and Pipeline
  - export Openshift GitOps Operator channel(e.g stable-4.7,preview 4.7) - ```export GITOPS_CHANNEL=stable-4.7```<br/>
  - ```oc apply -k https://github.com/redhat-canada-gitops/catalog/openshift-gitops-operator/overlays/$GITOPS_CHANNEL```

2 Install Sealed Secrets Operator
   

Application will show how we can use ArgoCD to deploy/test a flask application running on openshift and test a Tekton Pipeline with it, the Application being used is [testFlask](https://github.com/MoOyeg/testFlask.git)<br/>
This repo leverages sealed secret as mentioned earlier. I have included a sample private key to demo how sealed secrets can be stored in git and decrypted at runtime.Please do not store private keys in git.<br/>

## To Run Application
1 Clone this repo<br/>
2 Change directory into repo<br/>
2 Run ```kustomize build ./config/argocd | oc apply -f -```<br/>



