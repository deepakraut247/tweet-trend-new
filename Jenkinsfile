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
             stage("Jar Publish") {
            steps {
                script {
                        echo '<--------------- Jar Publish Started --------------->'
                         def server = Artifactory.newServer url:registry+"/artifactory" ,  credentialsId:"Jfrog_Cred"
                         def properties = "buildid=${env.BUILD_ID},commitid=${GIT_COMMIT}";
                         def uploadSpec = """{
                              "files": [
                                {
                                  "pattern": "jarstaging/(*)",
                                  "target": "libs-release-local/{1}",
                                  "flat": "false",
                                  "props" : "${properties}",
                                  "exclusions": [ "*.sha1", "*.md5"]
                                }
                             ]
                         }"""
                         def buildInfo = server.upload(uploadSpec)
                         buildInfo.env.collect()
                         server.publishBuildInfo(buildInfo)
                         echo '<--------------- Jar Publish Ended --------------->'  
                
                }
            }   
        }


    }
}
