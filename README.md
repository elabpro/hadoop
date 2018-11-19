# hadoop
Hadoop cluster with Spark (vagrant + ansible)

Video https://youtu.be/a3CLG-1AxmE

# Steps to create a cluster:

 -   Clone the repository
 -   cd cluster/
 -   vagrant up
 -   sh install_getfiles.sh
 -   ansible-playbook -i inventory/vagrant-4hosts.inv playbooks/hadoop.yml
 -   ssh -i ~/.vagrant.d/insecure_private_key vagrant@192.168.50.11
 -   vm# cd $HADOOP_INSTALL
 -   vm# sbin/start-all.sh
