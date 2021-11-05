# How To Install Jenkins
This is our internal documentation how to install Jenkins.
If you want to understand more there is a blog post that you can read and use this code for your own purpose.

## Install Using Helm
We are using Native Kubernetes and Helm to install our Jenkins Installation.
You can execute following command and using one of following configuration.

`helm install jenkins jenkins/jenkins -f config/values.yaml --wait`

## Install Using Operator
We are not using RedHat OpenShift or Minikube, but if you want to install Jenkins on Minikube or RedHat Openshift, you can follow this Installation guide from (Jenkins Doc Site)[https://www.jenkins.io/doc/book/installing/kubernetes/]

## Education
If you want to educate your self about Jenkins there is a lot of great material on the web like (Google Qwiklab)[https://googlecourses.qwiklabs.com/]. Or you have great Youtube channel from (CloudBees)[https://www.youtube.com/c/CloudBeesTV/featured] that explains multiple ways how to use Jenkins.

You have the official documentation about (Jenkins here)[https://www.jenkins.io/doc/]
