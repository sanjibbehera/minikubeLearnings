# minikubeLearnings

### Hello and Welcome to this Repo Page..
### Information is already there in the Kubernetes Page 'https://kubernetes.io' about how to setup/install/configure MINIKUBE.
#### This Repo page showcases my experience about how to setup MINIKUBE on Windows and Ubuntu Platform.
#### First we will start with WINDOWS OS. Below are the steps done by me.

#### Step 1. Prerequisites for MINIKUBE installation/configuration in Windows platform.
> Oracle Virtualbox or any other Hyper-V software must have been installed in windows.

> wmic.exe is used while configuring minikube, hence the path 'C:\Windows\system32\wbem'  
should be configured in PATH environment variable.

#### Step 2. Download kubectl and minikube exe files from the below URLs and keep it in C drive in a folder say Kubernetes.
> https://storage.googleapis.com/kubernetes-release/release/v1.17.0/bin/windows/amd64/kubectl.exe  
(download link for kubectl).

> https://github.com/kubernetes/minikube/releases/tag/v1.5.2  
(At the time of writing this, latest version for minikube was 1.5.2, hence download the minikube binary from assets section).

#### Step 3. Configure the minikube.
> Go to Kubernetes folder & execute the below command as shown in the below snip to configure minikube.
![alt text](https://github.com/sanjibbehera/minikubeLearnings/blob/master/minikube_successful_start.JPG)

> Check the status if the minikube is successfully configured, the below snip o/p states success.
![alt text](https://github.com/sanjibbehera/minikubeLearnings/blob/master/minikube_successful_configuration.JPG)

#### Step 4. Login to Minikube VM.
> Once the above step completes, you can see a new VM called minikube in Oracle Virtualbox in running state.  
There are 2 ways to connect it.

> Use command prompt from Kubernetes folder and issue the command 'minikube ssh'.

> launch the VM from Oracle Virtualbox and use the credentials. 'docker/tcuser'.
