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

## How to copy files from worker nodes (Linux and Windows) to local machine?
**1. You can copy files from Linux worker node by the following steps:**
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
  *Example:*
  ```
  kubectl cp connector-xxxxxx:/tmp/logs.zip /tmp/logs.zip
  ```
**2. You can copy files from Windows worker node by the following steps:**

*Note: Username and Password are required for Windows node.*
- Connect to the Windows node using kubectl enter command: 
  ```
  kubectl enter <windows-node>
  ```
- Open another shell and look for the connector-xxxxxx pod in default namespace: 
  ```
  kubectl get pod
  ```
- Exec to the connector pod which will be a Liunx node in your cluster:
  ```
  kubectl exec -it connector-xxxxxx -- bash
  ```
- Copy the file from Windows node to the Linux node using scp command:
  ```
  scp <WindowsNodeUserName>@<aksNodeOrIPaddress>:/FilePathOnWindowsNode /DestPathOnYourLinuxNode/Filename
  ```
  *Example:*
  ```
  scp azureuser@aksnp000000:/c:/Users/azureuser/aksn000000_logs.zip /tmp/aksnp000000_logs.zip
  ```
- Copy the file of Windows node from connector pod which will be the Linux worker node to your local machine:
  ```
  kubectl cp connector-xxxxxx:/FilePathOnLinuxNode /DestPathOnYourLoaclMachine/Filename
  ```
  *Example:*
  ```
  kubectl cp connector-xxxxxx:/tmp/aksnp000000_logs.zip /tmp/aksnp000000_logs.zip
  ```
