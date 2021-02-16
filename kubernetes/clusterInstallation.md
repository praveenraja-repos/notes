## First installation
### In Master

- Install kubeadm command

- We are goint to pull images for various components kube-apiserver, kube-controller-manager, kube-scheduler, etcd
    ```bash
    kubeadm config images pull
    ```

- For instaling the master component in master node
    ```bash
    kubeadm init  --pod-network-cidr=192.168.0.0/16
    ```
- When kubeadm init finishes we need to execute following instructions as mentioned in kubeadm init output.
    - Eg:
    ```bash
    mkdir -p $HOME/.kube

    cp -i /etc/kubernetes/admin.conf $HOME/.kube/config

    chown $(id -u):$(id -g) $HOME/.kube/config
    ```
- Create a network for IP-per-Pod criteria. 
    - For example, to use the Weave network, you would do the following: 
    ```bash
			§ kubectl create -f https://git.io/weave-kube 
    ```    
### In Worker

kubeadm join

## Upgrade
### kubeadm upgrade command

- This will check the installed version against the newest found in the repository, and verify if the cluster can be upgraded.
    ```bash
    kubeadm upgrade plan
    ```
- Upgrades the first control plane node of the cluster to the specified version.
    ```bash
    kubeadm upgrade apply
    ```
- Similar to an apply --dry-run, this command will show the differences applied during an upgrade.
    ```bash
    kubeadm upgrade diff
    ```
- This allows for updating the local kubelet configuration on worker nodes, or the control planes of other master nodes if there is more than one. Also, it will access a phase command to step through the upgrade process.
    ```bash
    kubeadm upgrade node
    ```

### Other commands  


