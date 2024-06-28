What is Apache Tomcat? A Beginner's Guide to the Web Server
"Exploring Apache Tomcat: Elevate Your Web Development Experienc
🚀🚀Deployment of Apache Tomcat Webserver

Apache Tomcat is a web server

Apache Tomcat is free and open source

Apache Tomcat runs on 8080 port by default (we can also change that port )

Apache Tomcat Folder Structure

bin : It contain commands to start and stop Tomcat server (if we are using windows then we use startup.bat and shutdown.bat )(if we are using Linux OS then we use startup.sh and shutdown.sh )

conf : It contains configuration files

lib : It contains libraries (jars files)

logs : It contains servers logs files

temp : Temp files will be created here (we can also delete them )

webapps : This is called as a deployment folder

Note : We will keep all war files in webapps folder for deployment , thats why webpps called deployment folder

Working with Apache Tomcat in Linux OS

Here , the steps we need to follow for set up tomcat

Login into AWS Management Console

Create EC2 Instance (Ubuntu or any AMI)

Connect to EC2 instance using Git-bash /putty / MobaXterm

Install java software using below command

sudo apt install java-1.8.0-openjdk

Verify the version of java installed in our machine

java -version

Note : If we have multiple java version installed then we can switch to particular version using below command

alternatives --config java

We can download Apache Tomcat from Official Website

https://tomcat.apache.org/download-90.cgi

We can find Apache Tomcat URLs to downloads in officials website downloads page

Copy the URL of tar file and execute below command in linux machine

wget< tomcat-tar-file-url>

After tomcat tar file got download the extract Tomcat Tar file using below command

 tar -xvf<tomcat-tar-file-name>

Go inside tomcat folder and see folder structure

$cd tomcat -folder

ls -lrt

Go to tomcat bin directory and run tomcat server

cd bin/

./startup.sh

Note : Tomcat server runs on 8080 port by Default . Enable this port in security group as custom tcp

Security Groups config

Type : Custom TCP

Portoal : TCP

Port Range : 8080

Source : Custom (0.0.0.0/0)

Access Tomcat server from your browser

URL : http : // EC2-VM-Public-IP :8080/

Note : It should open tomcat server home page .

By default the Host Manager is only accessible from a browser running on the same machine as Tomcat .

If you wish to modify this restriction , you 'll need to edit the Host Manager 's Context.xml file.

File Location : <Tomcat >/webapps/manager/META-INF/context.xml

      <context antiResourceLocking="false" privileged="true" >
          <valve className="org.apache.catalina.valves.RemoteAddrValve" allow".*"  />
      </context>

Add Tomcat Users in Tomcat/conf/tomcat/tomcat-users.xml file like below /

<role rolename="manager-gui" />
<user username="tomcat" password="tomcat" roles="manager-gui" />
<role rolename="divya-gui" />
<user username="divya" password="divya" roles="manager-gui,divya-gui" />

We can change tomcat servers default port in tomcat/conf/server.xml file

When We change tomcat port number in server.xml file then we have to enable that port in security Group which is associated with our EC2 Instance .

Steps to display Maven Web Application

Create Maven Web Application

Edit index.html file like below (File Location : project-folder\src\main\webapp)

<html>
<body>
<h1><font color='red'> Welcome to divyalearn.online...!! <font></h1>
<h2> Learn here .... Lead Anywhere ...!! </h2>
<a href="https://learnwithdivya.hashnode.dev"> click Here To see My Blogs</a>
</body>
</html>

package Maven Web Application as a war file using Maven Goals

mvn clean package

Go to Tomcat Server Admin Dashboard and click on "Manager App "

Select War file to upload and click on "Deploy" button

War file will be deployed and it will display in application

Click on Application Path (It will open the application in browser )

CONCLUSION
_________________________________________________________________________________________________________________________________________________________________________________________
Stop Apache Tomcat Server

Stop EC2 instance

________________________________________________________________________________________________________________________________________________________________________________________

😀❤️Happy coding 🎶💡📚

🌟 Connect with Us Across Platforms! 🌐

Looking to stay updated on industry insights, career opportunities, and more? Join our network on LinkedIn and other social platforms! 🚀

👔 Connect professionally with us on LinkedIn for the latest in DevOps trends and news. 📈 Let's build connections that matter!

💬 Follow us on LinkedIn --> https://www.linkedin.com/in/divya-satpute-68666a300/ to engage with our community and join the conversation on relevant topics. 🌍

Stay connected, stay informed, and let's grow together! 💡

👏 Bravo! Take a moment to bask in your success—it's well-deserved! 🌟

🎊 Celebrate your achievements with a victory dance! You've reached new heights! 🚀
