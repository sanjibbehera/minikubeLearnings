# minikubeLearnings

### Hello and Welcome to this Repo Page..
### Information is already there in the Kubernetes Page 'https://kubernetes.io' about how to setup/install/configure MINIKUBE.
#### This Repo page showcases my experience about how to setup MINIKUBE on Windows and Ubuntu Platform.

#### Part 1. First we will start with WINDOWS OS. Below are the steps done by me.

#### Step 1. Prerequisites for MINIKUBE installation/configuration in Windows platform.
> Oracle Virtualbox or any other Hyper-V software must have been installed in windows.

> check if Virtualization is supported on Windows 10 with <b>systeminfo</b> command.  
The below screenshot is from the long list o/p of <b>systeminfo</b> command, if the below is not shown  
then virtualization is not supported in your machine.
![alt text](https://github.com/sanjibbehera/minikubeLearnings/blob/master/hyperVrequirement_windows.JPG)

> If Virtualization is not enabled, open powershell or cmd as <b>administrator</b> and execute below command.  
<b>DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V</b>

> wmic.exe is used while configuring <b>minikube</b>, hence the path 'C:\Windows\system32\wbem'  
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

#### Step 5. Interact with Kubernetes Cluster with an existing image.
> <b> Find the nodes running in the cluster.</b>  
kubectl get nodes

> <b>create a Kubernetes Deployment using an existing image named echoserver,  
which is a simple HTTP server and expose it on port 8080 using --port</b>   
kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10

> <b>To access the hello-minikube Deployment, expose it as a service.</b>  
kubectl expose deployment hello-minikube --type=NodePort --port=8080

> <b>Check if the deployment is up and running using the below command.</b>  
kubectl get pod

> <b>Get the URL of the exposed Service to view the Service details.</b>  
minikube service hello-minikube --url

> <b>Delete the service of the deployment.</b>  
kubectl delete services hello-minikube

> <b>Delete the deployment.</b>  
kubectl delete deployment hello-minikube

#### Part 2. Next we will start with UBUNTU OS. Below are the steps done by me.

#### Step 1. Prerequisites for MINIKUBE installation/configuration in UBUNTU OS platform.
> Check virtualization is supported in linux, the below command's o/p must be blank.  
grep -E --color 'vmx|svm' /proc/cpuinfo

#### Step 2. Install kubectl.
