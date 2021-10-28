pipeline{
  agent any
  tools{
    maven 'maven'
  } 

  stages{
    stage('git'){
      steps{
        git 'https://github.com/nainala0594/jenkins-multi-pipeline.git'
      }
    }

    stage('build'){
      steps{
        sh 'mvn clean install package'
      }
    }

    stage('deploy'){
      steps{
        sshagent(['deployer_1']) {
          sh "scp -o StrictHostKeyChecking=no target/mahaLogin-1.0.war tomcat9@:35.175.242.143:/opt/tomcat8/webapps"
        }
      }
    }
  }
}
