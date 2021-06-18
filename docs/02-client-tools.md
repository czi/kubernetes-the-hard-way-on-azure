# Installing the Client Tools

In this lab you will install the command line utilities required to complete this tutorial: [cfssl](https://github.com/cloudflare/cfssl), [cfssljson](https://github.com/cloudflare/cfssl), and [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl).

## Install CFSSL

The `cfssl` and `cfssljson` command line utilities will be used to provision a [PKI Infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure) and generate TLS certificates.

Download and install `cfssl` and `cfssljson` from the [cfssl repository](https://github.com/cloudflare/cfssl/releases):

### OS X

OS X users may experience problems using the pre-built binaries in which case [Homebrew](https://brew.sh) might be a better option:

```
brew install cfssl
```

### Linux

```shell
wget -q --show-progress --https-only --timestamping \
  https://github.com/cloudflare/cfssl/releases/download/v1.4.1/cfssl_1.4.1_linux_amd64 \
  https://github.com/cloudflare/cfssl/releases/download/v1.4.1/cfssljson_1.4.1_linux_amd64
```

```shell
chmod +x cfssl_1.4.1_linux_amd64 cfssljson_1.4.1_linux_amd64
```

```shell
sudo mv cfssl_1.4.1_linux_amd64 /usr/local/bin/cfssl
```

```shell
sudo mv cfssljson_1.4.1_linux_amd64 /usr/local/bin/cfssljson
```

### Windows
For windows on 64 bit use powershell, using administrative rights
```shell
PS C:\Windows\system32>Invoke-WebRequest -Uri https://github.com/cloudflare/cfssl/releases/download/v1.4.1/cfssl_1.4.1_windows_amd64.exe -OutFile cfssl.exe
PS C:\Windows\system32>Invoke-WebRequest -Uri https://github.com/cloudflare/cfssl/releases/download/v1.4.1/cfssljson_1.4.1_windows_amd64.exe -OutFile cfssljson.exe
```


### Verification

Verify `cfssl` version 1.4.1 or higher is installed:

```shell
cfssl version
```

If this step fails with a runtime error, try installing cfssl following instructions on [CloudFlare's repository](https://github.com/cloudflare/cfssl#installation)

> output

```shell
Version: 1.4.1
Revision: dev
Runtime: go1.13.4
```

```shell
cfssljson -version
```

> output

```shell
Version: 1.4.1
Revision: dev
Runtime: go1.13.4
```

## Install kubectl

The `kubectl` command line utility is used to interact with the Kubernetes API Server. Download and install `kubectl` from the official release binaries:

### OS X

```shell
curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl"
```

```shell
chmod +x ./kubectl
```

```shell
sudo mv ./kubectl /usr/local/bin/kubectl
```

### Linux

```shell
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl
```

```shell
chmod +x ./kubectl
```

```shell
sudo mv ./kubectl /usr/local/bin/kubectl
```

### Windows
Note you need to have chocolately package manager installed first (https://chocolatey.org/)

```shell
PS C:\Windows\system32>choco install kubernetes-cli
```

### Verification

Verify `kubectl` version 1.21.0 or higher is installed:

```
kubectl version --client
```

> output

```
Client Version: version.Info{Major:"1", Minor:"21", GitVersion:"v1.21.0", GitCommit:"cb303e613a121a29364f75cc67d3d580833a7479", GitTreeState:"clean", BuildDate:"2021-04-08T16:31:21Z", GoVersion:"go1.16.1", Compiler:"gc", Platform:"linux/amd64"}
```

To quick check kubectl version, you can also use the following command : 

```shell
kubectl version --client --short
```

> output

```shell
Client Version: v1.21.0
```

Next: [Provisioning Compute Resources](03-compute-resources.md)
