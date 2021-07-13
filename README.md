# K8S Tutorial 3

### Switching context for kubectl
In order to access a different cluster you need to change kube config files. Kubectl config is by default stored in:
`~/.kube/config`
You should already have a config file for minikube so back it up by doing the following command:
`mv ~/.kube/config ~/.kube/mini-kube-backup`
This can be restored at any time with (will overwrite any existing config):
`mv ~/.kube/mini-kube-backup ~/.kube/config`

For our in person tutorials you should be sent an email containing a kube config file. Simply overwrite the default config with:
`mv my-config ~/.kube/config`

You can then test your config with the following command:
`kubectl version`

**Working output**
```
Client Version: version.Info{Major:"1", Minor:"21", GitVersion:"v1.21.2", GitCommit:"092fbfbf53427de67cac1e9fa54aaa09a28371d7", GitTreeState:"clean", BuildDate:"2021-06-16T12:59:11Z", GoVersion:"go1.16.5", Compiler:"gc", Platform:"darwin/amd64"}

Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.4", GitCommit:"d360454c9bcd1634cf4cc52d1867af5491dc9c5f", GitTreeState:"clean", BuildDate:"2020-11-11T13:09:17Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```
**Misconfigured config/directory**
```
Client Version: version.Info{Major:"1", Minor:"21", GitVersion:"v1.21.2", GitCommit:"092fbfbf53427de67cac1e9fa54aaa09a28371d7", GitTreeState:"clean", BuildDate:"2021-06-16T12:59:11Z", GoVersion:"go1.16.5", Compiler:"gc", Platform:"darwin/amd64"}

The connection to the server localhost:8080 was refused - did you specify the right host or port?
```

Once you have successfully added the appropriate kube config file you should be able to interact with the cluster via kubectl.

### Command Cheat Sheet


### Exploring an Existing Cluster
For this part of the tutorial you will be given access to an existing cluster. (if you are following this indepedently you will need access to a cluster with existing resources and kube-ctl set up).

### Accessing 

This tutorial consists of an activity to answer the following questions using kubectl that should leverage various commands above.

### Generic Questions
These questions can be asked if you are using any cluster.
#### Nodes
* How many nodes are in the cluster?
* How many nodes are worker nodes?
* How many pods are running on the control-plane nodes?
* What is the hostnames of the nodes with the etcd role?

#### Namespaces
* What namespaces are on the cluster?


#### Pods


### Specific Questions
This is for the in person tutorial scenario where specific access to our cluster has been given.

### Deployments


### Replica sets
