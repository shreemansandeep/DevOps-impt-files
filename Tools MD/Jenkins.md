jenkins ===>> CI / CD tool.

continueos intergration and continueos deployment tool.

jenkins is automation tool.

jenkins port number ==>> 8080

/etc/sysconfig/jenkins

jenkins ===>>> to overcome water fall model and agile methodologies ( draw backs / manual ) ===>> jenkins ( automation)..

Jenkins is the heart of the devops ..

we will integrate with all devops tools with jenkins and deploy the applications..==>> dev / Qa / uat / prod.

jenkins ==>> jobs create ==>> run ==>> build.

jenkins ==>> we have two types of jobs.

1. free style jobs ( jenkins dash board ===>>> GUI )

2. Pipeline jobs.. ( jenkins dash board ===>>> Groovy script and github ==>> jenkinsfile)

jenkins ===>> plugins ==>>> install ===>> extranal features adding to our jenkins dashboard.

jenkins ===>> plugins ==>>> 3 ways to install..

jenkins ==>> build triggers ===>> pollscm , build periodically ( cron expression ), webhooks..

jenkins ==>> all devops tool integrate with jenkins.

jenkins ==>>>> we will create parameterized jobs..

jenkins ==>>> sequential jobs ( upstream and downstream jobs) and parallel jobs..

jenkins ===>>> master / slave architecture.

jenkins ==>>> backup

jenkins ==>>> security.

jenkins ==>>> users to create.

jenkins ==>> upgrade.

jenkins ==>> automate with the help of jobs..

Jenkins ==>>> important configuration files..

1. jenkins home directory : /var/lib/jenkins.

2. installed plugins : /var/lib/jenkins/plugins

3. created jobs list : /var/lib/jenkins/workspace

4. nodes information : /var/lib/jenkins/nodes

5. jenkins logs information : /var/lib/jenkins/logs

6. list of jobs ==>> /var/lib/jenkins/jobs

7. created users list : /var/lib/jenkins/users.

Jenkins installation steps :

1. we need to take one ec2 instance and login into that ec2 instance.

2. java install

3. git install

4. maven install

5. jenkins install ( 4 steps)

6. start the jenkins service ==>>> service jenkins start

7. jenkins ec2instance==>> publicip:8080(  browser) ==>>> enter

8. jenkins dash board ==>> display ==>> path /var/lib/jenkins/secrets/initialadminpasswd ===>>> copy this path

9. go to jenkins ec2 instace ==>>> cat /var/lib/jenkins/secrets/initialadminpasswd ==>> enter ===>> encrypted password ==>> copy

10. paste it into jenkins dashboard ==>> box .

11. select suggested plugins ==>> click

12. username , password , conformpassword , email ===>> continure ==>> your jenkins dashboard is ready..

=================================================================================================================================

Automation project 1:

1. we need to create one ec2 instance and login into that ec2 instance===>> install tomcat.

2. we need to install deploy to container plugin in jenkins dashboard.( war file copy ==>>> source to destination)

3. create a jenkins job in jenkins dashboard.

===================================================================================================

pollscm : cron expression

build periodically : cron expression

webhooks : triggering concept ===>> we will create webhooks in github ===>> webhooks ==>> jenkins url ==>> event ==>> developer ==>> any modification ==>>> build trigger ==>> deployemnt..

********difference between pollscm ,build periodically , webhooks..

build periodically ==>> cron expression based ==>> schedule ==>> developer modify / un modify ==>>> automatically jobs ==>> build ==>>> deployments ==>>> jenkins instance ==>> CPU / DISK / MEMORY / NETWORK utilization increase ==>> jenkins instance hung state.

poll scm :==>> cron expression based ==>> schedule ==>> developer modify ==>>> automatically jobs ==>> build ==>>> deployments.

webhooks : event based ==>> developer ==>> any modification ==>> imediately action will takes palce.==>> jobs run ==>> deployments..

===========================================================================================================================

How to change jenkins port number ??

vi /etc/sysconfig/jenkins ===>> jenkins_port = 8080 ( 2005)

service jenkins stop

service jenkins start

==================================================================

parameterized builds :

we need to install git parameter plugin install..

senario :

developer ==>>> request raise to ops team ( ours)

can you please test the war file is generated or not  in dev / master / feture branch ??

========================================================================================================

sequential jobs / upstream and downstream jobs :

joba ==>> jobb ==>>> jobc ==>> continueosly loop.

Based on sequential jobs / upstream and downstream jobs  ===>>> visualization different.

we need to install two plugins..

1. buildpipeline plugin 

2. delivery pipeline plugin.

sequential jobs / upstream and downstream jobs ==>> continueosly loop.

jenkins instance ===>> CPU / DISK / MEMORY / NETWORK  utilization increase ==>> jenkins instance ==>>> hung state.

To over come above senario then parallel jobs came into the picture.

parallel jobs :

we need to install multi job plugin.

plugins extension ==>> .jpi or .hpi format

========================================================================================

Jenkins : master /slave concept.

master : jenkins install -->> instance ==>> master.

slaves / nodes ===>> another instances. ===>> we need to create slaves / nodes.

The main purpose of master/ slave is to distributing the builds.

===>> jenkins ==>> lot of jobs create ==>> load increase ==> more CPU / memory / network utilization increase ==>> jenkins instance ==>> hung state.

to over come this master / slave concept came into the picture.

By using master / slave concept ==> we will create the jobs in jenkins master and that jobs are build in nodes.

The communication between master and slave is SSH 

The communication between master and slave protocall is  TCP / IP

key point :1. we need to install jenkins in master only.

2. We need not to install jenkins on slave / nodes.

3. Basic rule : java installation is mandatory.

--->> master instance ==>> only one instance

===>> nodes will be n no.of instances.

==>> In real time each node can be treated as one environment.

Dev , QA , UAT , PROD.

===>>> each node ===>> tomcat instances.

The jobs are running between master and slave by using labels.

No operating system dependency between master and slaves / nodes.

jenkins ==>> linux and slaves ==>> windows ,centos , debian...etc.

=====================================================================================

How to create users in jenkins ??

jenkins dashboard ==>> manage jenkins ==>> manage users ==> create user ==>> bhargavi , password , conform password , email..

==========================================================================================

how take backup of the jenkins instance.

Backup ==>>> plugin ===>>> thinbackup plugin will install.

=============================================================================================================

How to provide security to the jenkins instance..

1. Autherization.

2. Authentication.

3. security realrms

4. role based strategy plugins.

1. Autherization. ===>>> IBM emp ==>>>> empid ===>> correct or not..

2.  Authentication. ==>> jenkins passowrd ==>> correct or not.

3. security realrms ===> LDAP / AD ===>> every 3 months once will change the passowrd. ===>>> the password comes from ldap / AD or not.

4. role based strategy plugins. : intsall ==>> dev enviroment or QA or UAT or PROD. ===>> which types environment you have the access.

=============================================================================================================

*******************Jenkins ===>> plugins installation ways are 3 types..


1. managejenkins ==>>> manage plugins ==>> available section ==>>> plugin name type ==>> install.

2. we need to download the plugin in our local laptop ==>> download and it is uploaded into the jenkins dash board.

 managejenkins ==>>> manage plugins ==>> advanced section ==>>> plugin to upload.

jenkins dashboard. ==>>> restart.

3.we need to download the plugin in our local laptop ==>> and copy that plugin to jenkins instance ==>>>this path.==>> /var/lib/jenkins/plugins.

jenkins instances ==>>> restart.

=============================================================================================================

Jenkins pipeline:

pipeline as a code.

In jenkins ==> two types of pipelines 

1. Declarative pipeline  2. scriptive pipeline.

In this pipelines we will write Groovy script.

Pipeline : Pipeline is a code and it has set of stages and stages contains steps , steps will execute entire pipeline.

stages example :

git clone url ( git checkout)

build

deploy..
==============================================================

steps step ( gitcheckout)

git clone url

step ( build)

mvn clean package

deploy 

war file copy ( by using scp)

==============================================================

pipeline ===>> Declarative 

pipeline ===>> node ===>> scriptive pipeline

agent : any , none , lable , docker

jenkinsfile extension : Jenkinsone or Jenkinsfile1 or Jenkins-123


1. Declarative pipeline :

we will create Jenkinsfile in github .

Jenkinsfile1

pipeline {

agent any

stages{

stage (gitcheckout)
{
step ()
git clone url

}

stage ( build )

{

step (build)

mvn clean package

}

steage ( deploy)

step ()

{

scp source destination 

tomcat servie start

}

}


==========================================================

2. Scriptive pipeline ==>> it is write in jenkins dash board.

node {

agent any

stages{

stage (gitcheckout)
{
step ()
git clone url

}

stage ( build )

{

step ()

mvn clean package

}

steage ( deploy)

step ()

{

scp source destination 

tomcat servie start

}

}


============================================================================================

pipeline ===>>> warfile copy ==>> we need to install ==>> SSH agent plugin install.


git credentialsId: 'javahome2', url: 'https://github.com/srinivas1987devops/myweb.git'

chown -R ec2-user:ec2-user apache-tomcat-9.0.41


==================================================================================================

How to upgarde the jenkins instance ??

jenkins version ==>> 2 after some time==>>  jenkins version 3


1. jenkins version 2 instance ==>> health checkup ( backup ) ===>> AMI / Image.

2. we need to create one ec2 instance ==>> login into that instance ==>> install jenkins version 3

3. jenkins version 2 ==>> Copy the contents of /var/lib/jenkins ===>> jenkins version 3 ==>>> /var/lib/jenkins

4. plugins also copy from jenkins 2 to jenkins version 3.

installed plugins from jenkins 2 /var/lib/kenkins/plaugins ===>>jenkins version 3 ==>> /var/lib/jenkins/plugins

5. Jenkins version 3 instance ==>> reboot ==>> properly work ==>> jenkins version2 instance ==>> delete.

=========================================================================================================


