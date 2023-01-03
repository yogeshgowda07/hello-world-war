pipeline {
    agent any
    stages {
        stage('clone step') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/venkibiligere/hello-world-war.git'
            }
        }
  stage('Build') {
            steps {
                sh 'mvn package'
            }
  }
//       stage('Deploy step') {
//             steps {
//                 sh 'sudo mv /var/lib/jenkins/${job_name}/hello-world-war-1.0.0.war /root/workspace/Slavejob/target/hello-world-war1-1.0.0.war'
//                 sh 'sudo cp /root/workspace/Slavejob/target/hello-world-war1-1.0.0.war /var/lib/tomcat9/webapps'      
//             }
//         }
    }
}
