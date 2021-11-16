pipeline {
    agent any
    tools { 
      maven 'MAVEN_HOME'
      jdk 'JAVA_HOME'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean'
                sh 'echo $JAVA_HOME'
                sh 'mvn clean package -DskipTests spring-boot:repackage'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Deliver') {
            steps {
                sh 'JENKINS_NODE_COOKIE=dontKillMe nohup mvn spring-boot:run >> ./testlog.log 2>&1 &'
            }
        }
    }
}
