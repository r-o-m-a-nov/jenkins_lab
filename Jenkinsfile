pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo "GIT_COMMIT: ${env.GIT_COMMIT}"
                echo "GIT_URL: ${env.GIT_URL}"

                echo 'Hello World'
                sh 'git tag v0.1'
                sh 'git branch v0.2-rc1'
                sh 'git branch'
                //sh 'git checkout main'
                //sh 'git pull'
                sh 'git push origin v0.1'
                sh 'git push --set-upstream origin v0.2-rc1'
                //sh 'git push --set-upstream origin main'
                
              }
        }
    }
}
