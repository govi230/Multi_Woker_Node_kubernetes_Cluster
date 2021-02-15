# Multi Woker Node kubernetes Cluster
Visit this link to know how to use Ansibel Role "kubernetes" to [SetUP Multi Node Kubernetes Cluster With the Help Of Ansible on AWS EC2 instances]()  

## Overview About "kubernetes" Ansible Role  
### Container Runtime Engine  
This Role right now only supports "[docker](https://docs.docker.com/get-started/overview/)" as Container Runtime Engine . To tell ot this Ansible Role  it give a varibale "**container_runtime_engine**".  By default this role use "docker" engine if you don't specify "container_runtime_engine" variable .
Eg-  container_runtime_engine: "docker"  
### Container Network Interface  
Right Now only "[flannel](https://github.com/coreos/flannel#flannel)" Container Network Interface is supported by this Role . "**container_netwrok_interface**" variable is available to tell this role which Container Network Interface will used to setup kubernetes cluster . By default this role use "**flannel**" network interface if you don't specify "container_runtime_engine" variable .
### Intialize Info  
To give Initialization Information to Role , it has "**init_info**" vaiable . This variable take multiple Arguments -
- **apiserver_advertise_address**  ->  The IP address the API Server will advertise it's listening on. If not set the default network interface will be used.
- **apiserver_bind_port**  ->  Port for the API Server to bind to. (default 6443)
- **apiserver_cert_extra_sans**  ->  Optional extra Subject Alternative Names (SANs) to use for the API Server serving certificate. Can be both IP addresses and DNS names.
- **cert_dir**  ->  The path where to save and store the certificates. (default "/etc/kubernetes/pki")
- **certificate_key**  ->  Key used to encrypt the control-plane certificates in the kubeadm-certs Secret.
- **config**  ->  Path to a kubeadm configuration file.
- **control_plane_endpoint**  ->  Specify a stable IP address or DNS name for the control plane.
- **cri_socket**  ->  Path to the CRI socket to connect. If empty kubeadm will try to auto-detect this value; use this option only if you have more than one CRI installed or if you have non-standard CRI socket.
- **experimental_patches**  ->  Path to a directory that contains files named "target[suffix][+patchtype].extension". For example, "kube-apiserver0+merge.yaml" or just "etcd.json". "patchtype" can be one of "strategic", "merge" or "json" and they match the patch formats supported by kubectl. The default "patchtype" is "strategic". "extension" must be either "json" or "yaml". "suffix" is an optional string that can be used to determine which patches are applied first alpha-numerically.
- **feature_gates**  ->  A set of key=value pairs that describe feature gates for various features. Options are:
                                             IPv6DualStack=true|false (ALPHA - default=false)
                                             PublicKeysECDSA=true|false (ALPHA - default=false)
- **ignore_preflight_errors**  ->  A list of checks whose errors will be shown as warnings. Example: 'IsPrivilegedUser,Swap'.
- **image_repository**  ->  Choose a container registry to pull control plane images from (default "k8s.gcr.io")
- **kubernetes_version**  ->  Choose a specific Kubernetes version for the control plane. (default "stable-1")
- **node_name**  ->  Specify the node name.
- **pod_network_cidr**  ->  Specify range of IP addresses for the pod network. If set, the control plane will automatically allocate CIDRs for every node. ( Required Parameter For this Role ) .
- **service_cidr**  ->  Use alternative range of IP address for service VIPs. (default "10.96.0.0/12")
- **service_dns_domain**  -> Use alternative domain for services, e.g. "myorg.internal". (default "cluster.local")
- **skip_phases**  ->  Don't print the key used to encrypt the control-plane certificates.
- **token**  ->  The token to use for establishing bidirectional trust between nodes and control-plane nodes. The format is [a-z0-9]{6}\.[a-z0-9]{16} - e.g. abcdef.0123456789abcdef
- **token_ttl**  ->  The duration before the token is automatically deleted (e.g. 1s, 2m, 3h). If set to '0', the token will never expire (default 24h0m0s).
- **upload_certs**  ->  Upload control-plane certificates to the kubeadm-certs Secret.
