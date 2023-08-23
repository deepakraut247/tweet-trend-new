pipeline {
    agent any

    environment{
        PATH = "/etc/maven/apache-maven-3.9.4/bin:$PATH"
    }

    stages {
    stage('build') {
        steps{
            sh 'mvn clean deploy'
        }
            
        }
    }
}
