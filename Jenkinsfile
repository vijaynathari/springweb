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
                sh 'mvn -version'
                sh 'java -version'
                sh 'mvn -DskipTests=true  package'
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
