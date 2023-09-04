def registry = 'https://rajdeep9898.jfrog.io/'
def imageName = 'rajdeep9898.jfrog.io/tweettrend-docker-local/ttrend'
def version   = '2.1.2'

pipeline {
    agent any

    environment{
        PATH = "/etc/maven/apache-maven-3.9.4/bin:$PATH"
    }

    stages {
    stage('build') {
        steps{
            sh 'mvn clean deploy -Dv=${BUILD_NUMBER}'
        }
            
        }



    }
}
