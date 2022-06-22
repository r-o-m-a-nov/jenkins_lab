pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
               //sh 'git tag v0.1'
                //sh 'git checkout -b v0.2-rc1'
                sh 'git branch'
                sh 'git push --set-upstream origin'
            }
        }
    }
}
