# Koding Kubernetes Config Files
Here you can find example configuration files for running Koding in a Kubernetes cluster.  These files should be considered to be for BETA testing and require some configuration before being able to run in an actual cluster.

## Important Notes about configuration
First, we do not recommend running our databases (postgres and mongo) on Kubernetes in a production environment since they store non-ephemeral data.  You should host them on more dedicated hardware.

Second, this setup requires the installation of Kubernetes addons such as KubeDNS.  Make sure these are installed and running on your system.  You can check this by examining the namespace kube-system and making sure there are kubelets running for the correct services.

Third, the versions of Mongo and Koding Docker images in these files are not up to date and should be adjusted to be so before deployment.

Fourth, you will have to determine based upon your setup how to expose koding-srv to the public.  In this example, all of the Kubernetes cluster's external IP addresses were added to the externalIPs field in koding-srv.yml.  You may want to specify which machine(s) Koding deploys to using a label and then add these externalIPs, or you can use a LoadBalancer if your cloud provider supports it.

Lastly, we recommend that you leave plenty of disk space on your VMs to run Koding.  You should have a minimum of 50GB of free disk space to install Koding.

##Launching
`kubectl create -f koding-kubernetes/`

##Contribution
Feel free to contribute additional examples under their own directories in this repository!
