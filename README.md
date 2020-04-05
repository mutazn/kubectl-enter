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

*You need to be able to start privileged containers for that.*
