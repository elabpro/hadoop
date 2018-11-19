# Hadoop + Spark
Hadoop cluster with Spark (vagrant + ansible)

Video https://youtu.be/a3CLG-1AxmE

Spark job for counting words with 2 and more vowels https://github.com/elabpro/hadoop/blob/master/cluster/playbooks/files/calc.py

# Steps to create a cluster

 -   Clone the repository
 -   cd cluster/
 -   vagrant up
 -   sh install_getfiles.sh
 -   ansible-playbook -i inventory/vagrant-4hosts.inv playbooks/hadoop.yml
 -   ssh -i ~/.vagrant.d/insecure_private_key vagrant@192.168.50.11
 -   vm# cd $HADOOP_INSTALL
 -   vm# sbin/start-all.sh

# How to test Hadoop cluster

 -   Prepare hdfs: bin/hdfs namenode -format
 -   Cleate input dir for data: bin/hdfs dfs -mkdir /in
 -   Put some info in it: bin/hdfs dfs -copyFromLocal /home/vagrant/books/* /in
 -   Run example: bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.9.1.jar wordcount /in /out
 -   See results: bin/hdfs dfs -ls /out
 -   Remove results: bin/hdfs dfs -rm -R /out

# How to test Spark cluster

 -   vm# spark-shell
 -   ss# var input = spark.read.textFile("/in/somefile.txt")
 -   ss# input.filter(line => line.length()>0).count()
