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

> <b>wmic.exe</b> is used while configuring <b>minikube</b>, hence the path 'C:\Windows\system32\wbem'  
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
> Check Virtualization is supported in linux, the below command's o/p must be blank.  
grep -E --color 'vmx|svm' /proc/cpuinfo

#### Step 2. Install kubectl. 
> <b>use the below command to download kubectl binary.</b>  
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

> <b>Make the kubectl binary executable.</b>  
chmod +x kubectl

> <b>Move the binary to PATH environment variable</b>  
sudo mv ./kubectl /usr/local/bin/kubectl

#### Step 3. Install Virtualbox.
> <b>Download Virtualbox 6.0.14 for ubuntu using below link.</b>  
https://download.virtualbox.org/virtualbox/6.0.14/virtualbox-6.0_6.0.14-133895~Ubuntu~bionic_amd64.deb

> Before installing ensure below packages are already installed in Ubuntu 18.04.  
<b>libqt5core5a (>= 5.9.0~beta)</b>  
<b>libqt5gui5 (>= 5.4.0)</b>  
<b>libqt5opengl5 (>= 5.0.2)</b>  
<b>libqt5printsupport5 (>= 5.0.2)</b>  
<b>libqt5widgets5 (>= 5.7.0)</b>  
<b>libqt5x11extras5 (>= 5.6.0)</b>  
<b>libsdl1.2debian (>= 1.2.11)</b>  

> <b>If the above libs are not installed, please execute the below command.</b>  
sudo apt-get install libqt5opengl5 libqt5printsupport5 libqt5widgets5 libqt5x11extras5 libsdl1.2debian libqt5core5a libqt5gui5 libdouble-conversion1 libqt5dbus5 libqt5network5 libxcb-xinerama0 qtbase-abi-5-9-5

> Install the debian package of Virtualbox using below cmd.  
sudo dpkg -i virtualbox-6.0_6.0.14-133895~Ubuntu~bionic_amd64.deb

#### Step 4. Install Minikube.
> Download minikube using the below command.  
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
  
> add minikube to PATH.  
sudo install minikube /usr/local/bin/

> start minikube and check status.  
<b>minikube start --vm-driver=virtualbox</b>  
<b>minikube status</b>  ##below should be the o/p:

host: Running  
kubelet: Running  
apiserver: Running  
kubeconfig: Configured

