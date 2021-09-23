# testFlask-Gitops
Sample Openshift-Gitops(ArgoCD) for a Flask Python Application  

## Pre-Requisites  

Openshift Pipelines Operator:<https://docs.openshift.com/container-platform/4.6/pipelines/installing-pipelines.html>  

Openshift GitOps Operator:<https://docs.openshift.com/container-platform/4.7/cicd/gitops/understanding-openshift-gitops.html>  

Sealed Secrets Operator: <https://github.com/bitnami-labs/sealed-secrets>  

Pipeline requires a default storage class.

## Pre-Requisites Sample Installation  
  
If using the Sealed Secrets Option, create the demo master key and RoleBinding for ArgoCD on namespace  

- ```export NAMESPACE="sealed-secrets"```  
  
- ```curl https://raw.githubusercontent.com/MoOyeg/testflask-gitops/main/environments/sealedsecret/env/base/100-sealedsecret-role-workaround.yaml | sed 's/namespace: sealed-secrets/namespace: "'"$NAMESPACE"'"/' | oc apply -n $NAMESPACE -f -```  

- ```curl https://raw.githubusercontent.com/MoOyeg/testflask-gitops/main/environments/sealedsecret/env/base/100-sealedsecret-rolebinding-workaround.yaml | sed 's/namespace: sealed-secrets/namespace: "'"$NAMESPACE"'"/' | oc apply -n $NAMESPACE -f -```  

- ```curl https://raw.githubusercontent.com/MoOyeg/testflask-gitops/main/environments/sealedsecret/env/base/500-sealedsecret-mastersecret.yaml | sed 's/namespace: sealed-secrets/namespace: "'"$NAMESPACE"'"/' | oc apply -n $NAMESPACE -f -```  

Application will show how we can use ArgoCD to deploy/test a flask application running on openshift and test a Tekton Pipeline with it, the Application being used is [testFlask](https://github.com/MoOyeg/testFlask.git)  
This repo leverages sealed secret as mentioned earlier. I have included a sample private key to demo how sealed secrets can be stored in git and decrypted at runtime.Please do not store private keys in git.  

## To Run Application

1 Clone this repo  
2 Change directory into repo  
2 Run ```kustomize build ./config/argocd | oc apply -f -```  
