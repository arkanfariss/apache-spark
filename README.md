~~ Apache Spark ~~

sudo apt update

sudo apt install default-jdk

java --version

curl -O https://downloads.apache.org/spark/spark-2.4.7/spark-2.4.7-bin-hadoop2.7.tgz 
tar xvzf spark-2.4.7-bin-hadoop2.7.tgz 
sudo mv spark-2.4.7-bin-hadoop2.7 /opt/spark
cd /opt/spark/
sudo sbin/start-master.sh
ss -tunelp |grep 8080
cat /opt/spark/logs/spark-root-org.apache.spark.deploy.master.Master-1-iz8psi2f05o3u4ekqki8k8Z.out
sudo sbin/start-slave.sh spark://sparktesting.dmxonqygcr0ehciiwimzfeacqd.bx.internal.cloudapp.net:7077
pico input.txt
bin/spark-shell
val inputfile = sc.textFile(“input.txt”)
val counts = inputfile.flatMap(line => line.split(" ")).map(word => (word, 1)).reduceByKey(_+_);
counts.cache()
counts.saveAsTextFile("output")
cd output/
cat part-00000
