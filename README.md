# How To Install Jenkins
This is our internal documentation how to install Jenkins.
If you want to understand more there is a blog post that you can read and use this code for your own purpose.

![Jenkins Logo](img/jenkins.png?raw=true)

## Install Using Helm
We are using Native Kubernetes and Helm to install our Jenkins Installation.
Download this repo where you have helm installed. [Installing Helm](https://helm.sh/docs/intro/install/)

When you have download the configuration file(s) you can either run following command to have full deployment running in Kubernetes both Jenkins Server and Jenkins Cloud Agent.

Create a namespace where you want to deploy Jenkins.

`kubectl create namespace <namespace name>`

Make that namespace to your default working namespace for `kubectl` and `helm`.

`kubectl config set-context --current --namespace=<namespace name>`

Install Jenkins, make sure you use `--wait` anotherwise you have no idea when the installation is done.

`helm install <name> jenkins/jenkins -f config/values.yaml --wait`

If you only want to install a basic installation of Jenkins Server without extra configuration you can then run following command.

`helm install <name> jenkins/jenkins -f config/values_minimal.yaml --wait`

To show the password that has been generated you can run following command.

`kubectl exec --namespace <namespace> -it svc/<name> -c jenkins -- /bin/cat /run/secrets/chart-admin-password && echo`

This command should also been printed on your screen when the installation is done.

The installation takes a wild, it is perfect moment to grab a cup of coffee.
When the installation are done you need to configure Jenkins service account to be able to deploy agents to the cluser.

`kubectl create clusterrolebinding jenkins-deploy --clusterrole=cluster-admin --serviceaccount=default:cd-jenkins`

### Test the Installation
When the installation is done, you can easy test your installation by running port-forward command.

`kubectl --namespace <Jenkins Namespace> port-forward svc/<Jenkins Service Name> 8080:8080`

This command is also printed on your screen so you easy can copy and paste the command.

[Login to http://127.0.0.1:8080](http://127.0.0.1:8080)

## Install Using Operator
We are not using RedHat OpenShift or Minikube, but if you want to install Jenkins on Minikube or RedHat Openshift, you can follow this Installation guide from [Jenkins Doc Site](https://www.jenkins.io/doc/book/installing/kubernetes/)

## Education
If you want to educate your self about Jenkins there is a lot of great material on the web like [Google Qwiklab](https://googlecourses.qwiklabs.com/). Or you have great Youtube channel from [CloudBees](https://www.youtube.com/c/CloudBeesTV/featured) that explains multiple ways how to use Jenkins.

You have the official documentation about [Jenkins here](https://www.jenkins.io/doc/)
Unfortunately there is no official Slack channel for Jenkins but there is a [Gitter Channel](https://gitter.im/jenkinsci/newcomer-contributors) that you can join.
