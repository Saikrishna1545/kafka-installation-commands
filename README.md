# kafka-installation-commands
This stores basic instructions to install kafka locally on your desktop.

1. Use this website to download the software: https://kafka.apache.org/quickstart Place the .tgz file in your C folder
2. Then run the following 2 commands in Git Bash to extract the files out of the .tgz file:
```
$ tar -xzf kafka_2.13-2.7.0.tgz
$ cd kafka_2.13-2.7.0
```
4. Once this is done, change the System Environment Settings as instructed below:
```
Windows + Edit the System Environment Variables / Environment Variables / System variables (bottom half). Note:  Use the version you installed in the following. 

1. JAVA_HOME = C:\Program Files\OpenJDK\jdk-version folder
2. KAFKA_HOME =  C:\kafka-version folder
3. M2_HOME = C:\ProgramData\chocolatey\lib\maven\apache-maven-version
4. Path - must include (make sure you have only one JDK location in your path!)
    %JAVA_HOME%\bin OR C:\Program Files\OpenJDK\jdk-version\bin (or similar, NOT both!)
    %M2_HOME%\bin
    %KAFKA_HOME%\bin
    %KAFKA_HOME%\bin\windows
```
1. You can then use Powershell commands to start the program: (Open 5 different terminals in the kafka folder on your C drive.)
```
Window 1 - Run Zookeeper Service  (keep window open)
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties

Window 2 - Run Kafka Service (keep window open)
.\bin\windows\kafka-server-start.bat .\config\server.properties

Window 3 (temporary) - Execute One-Time Commands - create, list, delete topics 
.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --create --topic annies-thoughts
.\bin\windows\kafka-topics.bat --zookeeper localhost:2181 --list

Window 4 - Run Kafka Producer (will provide a > prompt for writing messages)
.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic annies-thoughts

Window 5 - Run Kafka Consumer (to show messages from the beginning)
.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic annies-thoughts --from-beginning
```
