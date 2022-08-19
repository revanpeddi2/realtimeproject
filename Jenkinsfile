pipeline{
    agent any
    tools{
     maven 'maven-3.8.6'
    }
    stages{
        stage("git clone"){
            steps{
                git credentialsId: 'GIT_CREDS2', url: 'https://github.com/revanpeddi2/realtimeproject.git'
            }
        }
        stage("maven build"){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("Tomcat war deployment"){
            steps{
             deploy adapters: [tomcat8(credentialsId: 'TOMCAT_CRED', path: '', url: 'http://ec2-3-110-189-170.ap-south-1.compute.amazonaws.com:8080')], contextPath: 'myapplication', war: '**/target/*.war'   
            }
        }  
    }
}
