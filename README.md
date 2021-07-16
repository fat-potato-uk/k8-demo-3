# K8S Tutorial 3

This tutorial focuses on using kubectl as a way to interact with a Kubernetes environment.
It works best with an existing, working cluster as this will contain a variety of deployments, 
pods and namespaces.

For those in instructor led tutorials, cluster access will be provided, for those following 
independently please use an example either created yourself or found on the internet.

### Prerequisites 

You will need kubectl installed. You can follow the instructions [here to install kubectl](https://github.com/fat-potato-uk/k8s-demo-1#kubectl).

### Switching context for kubectl

Kubectl uses a config file to manage access tokens and other cluster information. In this section
we will keep a copy of our original config and switch to use a config pre-made which will allow
us to connect to our example cluster.

In order to access a different cluster you need to change kube config files. Kubectl config is by default stored in: <br/>
`~/.kube/config`  <br/> <br/>
You should already have a config file for minikube so back it up by doing the following command:  <br/>
`mv ~/.kube/config ~/.kube/mini-kube-backup`  <br/> <br/>
This can be restored at any time with (will overwrite any existing config):  <br/>
`mv ~/.kube/mini-kube-backup ~/.kube/config`  <br/>
 <br/> <br/>
For our in person tutorials you should be sent an email containing a kube config file. Simply overwrite the default config with:  <br/>
`mv my-config ~/.kube/config`
 <br/> <br/>
You can then test your config with the following command: <br/>
`kubectl version` <br/> <br/>

**Working output**

Note the values may differ slightly, the server information being present is a key indicator
the config is correct.
```
Client Version: version.Info{Major:"1", Minor:"21", GitVersion:"v1.21.2", GitCommit:"092fbfbf53427de67cac1e9fa54aaa09a28371d7", GitTreeState:"clean", BuildDate:"2021-06-16T12:59:11Z", GoVersion:"go1.16.5", Compiler:"gc", Platform:"darwin/amd64"}

Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.4", GitCommit:"d360454c9bcd1634cf4cc52d1867af5491dc9c5f", GitTreeState:"clean", BuildDate:"2020-11-11T13:09:17Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```
**Misconfigured config/directory**
```
Client Version: version.Info{Major:"1", Minor:"21", GitVersion:"v1.21.2", GitCommit:"092fbfbf53427de67cac1e9fa54aaa09a28371d7", GitTreeState:"clean", BuildDate:"2021-06-16T12:59:11Z", GoVersion:"go1.16.5", Compiler:"gc", Platform:"darwin/amd64"}

The connection to the server localhost:8080 was refused - did you specify the right host or port?
```

Once you have successfully added the appropriate kube config file you should be able to 
interact with the cluster via kubectl.

### Command Cheat Sheet
An in-depth cheatsheet for kubernetes is available [here](https://kubernetes.io/docs/reference/kubectl/cheatsheet/).


### Accessing 

This tutorial consists of answering the following questions using kubectl and the 
commands provided in the cheatsheet above. You will need to choose the right commands or 
combination of commands to get the answers

### Generic Questions

These questions can be asked if you are using **any** cluster. 
However, the spoiler answers provided are for the instructor led tutorial cluster.

#### Nodes

How many nodes are in the cluster?
<details>
  <summary>Answer</summary>
7

`kubectl get nodes` 
</details> <br>
How many nodes are worker nodes?
<details>
  <summary>Answer</summary>
 5

`kubectl get node --selector='node-role.kubernetes.io/worker'`
</details> <br>
How many pods are running on the control-plane nodes?
<details>
  <summary>Answer</summary>
5

`kubectl get pods --all-namespaces -o wide --field-selector spec.nodeName=NAME`
</details> <br>
What version of kubernetes is running on the nodes with the etcd role?
<details>
  <summary>Answer</summary>
1.19.4

`kubectl get nodes`
</details> <br>

#### Namespaces
What namespaces are on the cluster?
<details>
  <summary>Answer</summary>
<ol>
<li>cattle-logging
<li>cattle-system
<li>cert-manager
<li>default
<li>elastic-system
<li>fleet-system
<li>infrastructure
<li>ingress-nginx
<li>kube-node-lease
<li>kube-public
<li>kube-system
<li>observability
<li>opentelemetry-operator-system
<li>security-scan
<li>temp
<li>test
</ol> 

`kubectl get namespaces`
</details> <br>


#### Pods
How many pods are running in the default namespace?
<details>
  <summary>Answer</summary>
1

`kubectl get pods -n default`
</details> <br>

#### Replica sets
Are there any deployments with more than one replica in the test namespace? If so which?
<details>
  <summary>Answer</summary>
No, all the current replica sets only have one replica.

`kubectl get rs -n test`
</details>


