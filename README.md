# kubectl-enter

Start a root shell in the Kubernetes node's host OS running.

Compatible with Linux and Windows Kubernetes nodes.

## Installation

```
curl -LO https://raw.githubusercontent.com/mutazn/kubectl-enter/master/kubectl-enter
chmod +x ./kubectl-enter
sudo mv ./kubectl-enter /usr/local/bin/kubectl-enter
```

## Usage

```
kubectl-enter <node>
kubectl enter <node>

```
*Note: You need to be able to start privileged containers for that.*

## How to copy files from worker nodes to local machine?
**1.** You can copy files from Linux worker node by the following steps:
- Connect to the Linux node using kubectl enter command: 
  ```
  kubectl enter <node>
  ```
- Open another shell and look for the connector-xxxxxx pod in default namespace: 
  ```
  kubectl get pod
  ```
- Copy the file from connector pod which will be the Linux worker node to your local machine:
  ```
  kubectl cp connector-xxxxxx:/FilePathOnLinuxNode /DestPathOnYourLoaclMachine/Filename
  ```
