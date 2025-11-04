4.Compile project in Jenkins using Maven

go to manage Jenkins -> tools -> add JDK path (not bin) 
add maven
apply 
save
click on new item 
select free style project
create project
go to source code management
select git
paste your git repo link (it should contain pom.xml file)
set branch specifier based on GitHub repo (master/main)
add build step - top level maven - version:maven - goals: compile/clean compile exec:java -Dexec.mainClass=Main
apply
save
build now
console output

---------------------------------------------------------------------------------------

5. Create slave node in Jenkins

First go to manage Jenkins
click on nodes
create new node
select permanent agent and create
paste "C:\Program Files\Jenkins" in remote node directory and save
click on the node name 
copy the windows command and paste in CMD
Output 
info: connected (on terminal after command is executed)

---------------------------------------------------------------------------------------

6. Assign project to slave node and build project

First go to manage Jenkins
click on nodes
create new node
select permanent agent and create
paste "C:\Program Files\Jenkins" in remote node directory and save
click on the node name 
copy the windows command and paste in CMD

On home page click on New Item
enter name and select freestyle project 
tick "Restrict where this project can be run" and enter node name and save
click on build now
create a java file 

public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}

save as Hello.java in C:\Program Files\Jenkins\workspace\"project created"
go to configure and click on build steps
click on add build step and select "execute windows batch command"
type
>javac Hello.java
>java Hello
now click on apply
and again click on build
go to status and click the first link
and check console output
---------------------------------------------------------------------------------------

7. Run Selenium Tests in Jenkins Using Maven


go to manage Jenkins -> tools -> add JDK path (not bin) 
add maven
apply 
save


1) put these in GitHub first

> pom.xml 
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>selenium-demo</artifactId>
  <version>1.0</version>

  <dependencies>
    <!-- Selenium Java -->
    <dependency>
      <groupId>org.seleniumhq.selenium</groupId>
      <artifactId>selenium-java</artifactId>
      <version>4.25.0</version>
    </dependency>

    <!-- TestNG (you can use JUnit instead) -->
    <dependency>
      <groupId>org.testng</groupId>
      <artifactId>testng</artifactId>
      <version>7.10.2</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>3.2.5</version>
        <configuration>
          <includes>
            <include>**/*Test.java</include>
          </includes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>

create this path src/test/java/com/example/LoginTest.java

>LoginTest.java

package com.example;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.Test;

public class LoginTest {
    @Test
    public void openGoogle() {
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.google.com");
        System.out.println("Title: " + driver.getTitle());
        driver.quit();
    }
}

2) Jenkins
create new freestyle item -> configure -> put this GitHub's link in git repo url -> check for 'branches to build' should be main/master -> apply and save
now click on build



---------------------------------------------------------------------------------------

8. Build pipeline project in Jenkins

new item
pipeline
ok
triggers
trigger script

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Running') {
            steps {
                echo 'Running World'
            }
        }
    }
}

apply save
build now
check console

---------------------------------------------------------------------------------------
16. Set up a basic CI pipeline using a CI/CD tool 

new item
pipeline
ok
triggers
trigger script

pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/username/repo-name'
            }
        }
        stage('Check Java Version') {
            steps {
                bat 'java -version'
                bat 'javac -version'
            }
        }
        stage('Build') {
            steps {
                bat 'javac hello.java'
            }
        }
        stage('Run') {
            steps {
                bat 'java hello'
            }
        }
    }

    post {
        success {
            echo ' Pipeline executed successfully!'
        }
        failure {
            echo ' Pipeline failed!'
        }
    }
}

apply save
build now
check console
---------------------------------------------------------------------------------------


1. Create AWS instance and connect it to putty

create instance with ubuntu 
create key pair and select .ppk
click on instance
now copy the Public IPv4 address
open PuTTy 
paste the Public IPv4 address in HostName
now click on connection -> SSH -> Auth -> Credentials
now click on browse private key and select the downloaded ppk file
click on open
password: ubuntu
>nano msg
>cat msg

2. Install Docker on AWS instance and show the version of it.

create instance with ubuntu and connect
paste the following commands
>sudo su
>apt update -y
>apt install docker.io -y
>docker --version
>systemctl enable docker
>systemctl start docker
>systemctl status docker

3. Install git on AWS instance and show the version of it

create instance with ubuntu and connect
paste the following commands
>sudo su
>sudo apt update -y
>sudo apt install git -y
>git --version

-------------------------------------------------------------------------------------------


Github

11. Pull files from GitHub using git, make changes and push file to GitHub using git

make folder and open cmd in it

> git clone https://github.com/username/repo-name.git
> cd repo-name
> echo "Hello from Git" > readme.txt
> git status
> git add .
> git commit -m "New file"
> git push origin main/master
now create a file on GitHub repo and then
> git pull origin main/master

----------------------------------------------------------------------------------------------------

9. To Perform various GIT operations on local and Remote repositories

make a repo on github

local repo

> git config --global user.name "Your Name"
> git config --global user.email "your_email@example.com"
> mkdir myproject
> cd myproject
> git init
> echo "Hello from Git" > readme.txt
> git status
> git add .
> git commit -m "New file"
> git remote add origin https://github.com/USERNAME/REPO.git
> git push origin main/master


remote repo

make folder and open cmd in it

> git clone https://github.com/username/repo-name.git
> cd repo-name
> echo "Hello from Git" > readme.txt
> git status
> git add .
> git commit -m "New file"
> git push origin main/master
now create a file on GitHub repo and then
> git pull origin main/master

----------------------------------------------------------------------------------------------------

15. Create a Git repository, add a new file to the repository, Commit the changes with a
meaningful message, Push the changes to a remote repository.


make a repo on github

> git config --global user.name "Your Name"
> git config --global user.email "your_email@example.com"
> mkdir myproject
> cd myproject
> git init
> echo "Hello from Git" > readme.txt
> git status
> git add .
> git commit -m "New file"
> git remote add origin https://github.com/USERNAME/REPO.git
> git push origin main/master

----------------------------------------------------------------------------------------------------

14. Execute basic commands in git

> git --version
> git config --global user.name "Your Name"
> git config --global user.email "your_email@example.com"

> mkdir project
> cd project
> git init

> echo "sample text" > file.txt
> git status
> git add file.txt
> git add . 

> git commit -m "Initial commit"

> git log
> git branch

> git remote add origin https://github.com/USERNAME/REPO.git
> git remote -v

> git push -u origin main
> git push origin main
> git pull origin main

> git fetch
> git clone https://github.com/USERNAME/REPO.git



4.Compile project in Jenkins using Maven

go to manage Jenkins -> tools -> add JDK path (not bin) 
add maven
apply 
save
click on new item 
select free style project
create project
go to source code management
select git
paste your git repo link (it should contain pom.xml file)
set branch specifier based on GitHub repo (master/main)
add build step - top level maven - version:maven - goals: compile/clean compile exec:java -Dexec.mainClass=Main
apply
save
build now
console output

---------------------------------------------------------------------------------------

5. Create slave node in Jenkins

First go to manage Jenkins
click on nodes
create new node
select permanent agent and create
paste "C:\Program Files\Jenkins" in remote node directory and save
click on the node name 
copy the windows command and paste in CMD
Output 
info: connected (on terminal after command is executed)

---------------------------------------------------------------------------------------

6. Assign project to slave node and build project

First go to manage Jenkins
click on nodes
create new node
select permanent agent and create
paste "C:\Program Files\Jenkins" in remote node directory and save
click on the node name 
copy the windows command and paste in CMD

On home page click on New Item
enter name and select freestyle project 
tick "Restrict where this project can be run" and enter node name and save
click on build now
create a java file 

public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}

save as Hello.java in C:\Program Files\Jenkins\workspace\"project created"
go to configure and click on build steps
click on add build step and select "execute windows batch command"
type
>javac Hello.java
>java Hello
now click on apply
and again click on build
go to status and click the first link
and check console output
---------------------------------------------------------------------------------------

7. Run Selenium Tests in Jenkins Using Maven


go to manage Jenkins -> tools -> add JDK path (not bin) 
add maven
apply 
save


1) put these in GitHub first

> pom.xml 
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>selenium-demo</artifactId>
  <version>1.0</version>

  <dependencies>
    <!-- Selenium Java -->
    <dependency>
      <groupId>org.seleniumhq.selenium</groupId>
      <artifactId>selenium-java</artifactId>
      <version>4.25.0</version>
    </dependency>

    <!-- TestNG (you can use JUnit instead) -->
    <dependency>
      <groupId>org.testng</groupId>
      <artifactId>testng</artifactId>
      <version>7.10.2</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>3.2.5</version>
        <configuration>
          <includes>
            <include>**/*Test.java</include>
          </includes>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>

create this path src/test/java/com/example/LoginTest.java

>LoginTest.java

package com.example;

import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.Test;

public class LoginTest {
    @Test
    public void openGoogle() {
        WebDriver driver = new ChromeDriver();
        driver.get("https://www.google.com");
        System.out.println("Title: " + driver.getTitle());
        driver.quit();
    }
}

2) Jenkins
create new freestyle item -> configure -> put this GitHub's link in git repo url -> check for 'branches to build' should be main/master -> apply and save
now click on build



---------------------------------------------------------------------------------------

8. Build pipeline project in Jenkins

new item
pipeline
ok
triggers
trigger script

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

        stage('Running') {
            steps {
                echo 'Running World'
            }
        }
    }
}

apply save
build now
check console

---------------------------------------------------------------------------------------
16. Set up a basic CI pipeline using a CI/CD tool 

new item
pipeline
ok
triggers
trigger script

pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/username/repo-name'
            }
        }
        stage('Check Java Version') {
            steps {
                bat 'java -version'
                bat 'javac -version'
            }
        }
        stage('Build') {
            steps {
                bat 'javac hello.java'
            }
        }
        stage('Run') {
            steps {
                bat 'java hello'
            }
        }
    }

    post {
        success {
            echo ' Pipeline executed successfully!'
        }
        failure {
            echo ' Pipeline failed!'
        }
    }
}

apply save
build now
check console
---------------------------------------------------------------------------------------


1. Create AWS instance and connect it to putty

create instance with ubuntu 
create key pair and select .ppk
click on instance
now copy the Public IPv4 address
open PuTTy 
paste the Public IPv4 address in HostName
now click on connection -> SSH -> Auth -> Credentials
now click on browse private key and select the downloaded ppk file
click on open
password: ubuntu
>nano msg
>cat msg

2. Install Docker on AWS instance and show the version of it.

create instance with ubuntu and connect
paste the following commands
>sudo su
>apt update -y
>apt install docker.io -y
>docker --version
>systemctl enable docker
>systemctl start docker
>systemctl status docker

3. Install git on AWS instance and show the version of it

create instance with ubuntu and connect
paste the following commands
>sudo su
>sudo apt update -y
>sudo apt install git -y
>git --version

-------------------------------------------------------------------------------------------