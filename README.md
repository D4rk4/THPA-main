Since THPA comprises of 2 components custom kube-controller-manager and scheduler-extender so 
we need to modify these:

# Collecting nodes traffic

- Copy kube-proxy binary file in kube-proxy directory to /usr/local/bin/ in  kube-proxy container running on each node and then reset it.

- Check that enpoint is created on each node whenever new deployment is created to make sure we configure correctly.

# set nodes label

- For worker nodes, set the following label to them: node-role.kubernetes.io/worker=true

# kube-controller-manager

- cd to kube-controller-manager directory.

- Unzip and copy binary file "kube-controller-manager" to home directory.

- Copy kube-controller-manager.yaml to /etc/kubernetes/manifests/

- After copying, the kube-controller-manager pod will automatically be restarted.

# scheduler-extender

- cd to scheduler-extender directory

- copy files "scheduler-extender-config.yaml" and "scheduler-extender-policy.json" to /etc/kubernetes/

- copy file "kube-scheduler.yaml" to /etc/kubernetes/manifests/

- cd to k8s-scheduler-extender directory

- execute "go build ."

- Run the executable file because the scheduler extender run as a server that is triggered whenever new pod need to be scheduled.

# Source code

- For kube-controller-manager: https://github.com/nclabteam/kubernetes.git 

- For scheduler-extender: https://github.com/nclabteam/k8s-scheduler-extender-example.git

- Please check experimental_setup.txt for configuring testbed
