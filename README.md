# HadoopProject
Using hadoop and mapreduce.

This is an example/tutorial examining hadoop and mapreduce in the hadoop ecosystem. 
This is a maven project built using IntelliJ IDE community edition. This project uses code from
apache hadoop which is modified for the purpose of this project. 

There is a lot to know about hadoop ecosystem and for more information visit https://hadoop.apache.org/ to
learn more about it. The purpose of this project is to focus on actual code and configuration for creating
and running an hadoop/mapreduce job on a local environment. Even though there are libraries and some very interesting 
projects to install and use hadoop in windows machines, I personally prefer to be on a linux environment to use
hadoop. Now, talking about an linux environment for hadoop is another question. 

For this project I am using WSL(Windows Subsystem for Linux). This is not the best choice, it is just a preference.

So the first step is to download hadoop. Go to http://www.apache.org/dyn/closer.cgi/hadoop/common/ and download from
a mirror. I have downloaded hadoop subversion 3.0.0 for this project. Please Make sure to read all prerequisites before
installing hadoop. This project uses java 8 and hadoop 3.0.0.  

After installing hadoop and running the hadoop command to make sure it works we start IntelliJ and build a maven
project for WordCount. Hadoop can be run as a stand alone or as a pseudo-distributed mode. The detailed difference 
between the two is not very important for the purpose of this project. For this project we are running hadoop on a 
single machine so it does not really matter which of two modes we use. If we run it as a standalone then hdfs is not
used. In a pseudo-distributed node dhfs is used (running it in pseudo-distributed node is closer to running it in a
real system). 

In maven we install all the required libraries (dependencies) and create the class WordCount which has other classes 
in it for map and reduce functionality. For the purpose of this project everything is in one file but for production
we need to use java best programming practices and create files for each class.

We build the project in maven and generate the .jar file for our hadoop/mapreduce. On the same folder level as the 
hadoop installation create another folder to export the .jar to be run in hadoop. in windows WSL we have access to
windows file system (/mnt/c/path/to/some/window/folder). So after we build the .jar file we move it or copy it to
the windows WSL file system (/home/usr/path/to/hadoop/installation). We also ned to create an input folder for input
hadoop uses for processing. Create two files there file01 and file02 with some text in it. 

Once the .jar file is there we run it with hadoop command (/bin/hadoop). Below is an example command.
    /bin/hadoop jar java_hadoop_intelliJ_project/HadoopProject-1.0-SNAPSHOT.jar \
    com.anaptec.gentihaddop.WordCount input/ output/
change package name to your package name if different (com.anaptec.gentihadoop -> your.package.name) 

After the command is run please examine the output folder for the results. 

NOTE*: If hadoop is configured and run pseudo-distributed mode, make sure that the node is started before running
       any commands. If one wants to go back to standalone mode for debugging purposes make sure that all configuration
       for pseudo-distributed mode are changed back in order to avoid connection errors.     
 
