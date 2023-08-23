pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        
    stage('clone repo') {
            steps {
                git branch: 'main', url: 'https://github.com/deepakraut247/tweet-trend.git'
            }
        }
    }
}
