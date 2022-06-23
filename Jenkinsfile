def count=5;

pipeline {
    agent any
    environment {
      int  n = 5
    }

    stages {
        stage('GET ENV') {
            steps {
                echo "GIT_COMMIT: ${env.GIT_COMMIT}"
                echo "GIT_URL: ${env.GIT_URL}"
                echo "BRANCH_NAME: ${env.BRANCH_NAME}"
                echo "GIT_BRANCH: ${env.GIT_BRANCH}"
                echo "GIT_PREVIOUS_COMMIT: ${env.GIT_PREVIOUS_COMMIT}"
                echo "GIT_PREVIOUS_SUCCESSFUL_COMMIT: ${env.GIT_PREVIOUS_SUCCESSFUL_COMMIT}"
                echo "BUILD_TAG: ${env.BUILD_TAG}"
                echo "BUILD_NUMBER: ${env.BUILD_NUMBER}"
            }
        }
        stage('Test') {
            steps {
                
                echo "Variable count: $count"
                echo 'Hello World'
                sh(returnStdout: true, script: "git tag --points-at")
                sh("git tag --contains $GIT_COMMIT")
                sh("git tag -a -f v0.'${count}+1' -m 'Iteration is ${env.n}' ")
                //sh("git tag --contains")
                //sh 'git tag v0.2'
                echo "${env.n}"
                println (count + 1)
            
                getSum(6)
                 sh "git branch v0.${env.n}+1-rc1"
                //sh 'git branch'
                //sh 'git checkout main'
                //sh 'git pull'
                //sh 'git push origin v0.1'
                //sh 'git push --set-upstream origin v0.2-rc1'
                //sh 'git push --set-upstream origin main'
            }
        }
        stage('PUSH') {
            steps {        
                sshagent(credentials: ["bc9480a8-21a8-4bfd-a4d7-fe18b4b7f7bc"]) {
                    //def repository = "git@" + env.GIT_URL.replaceFirst(".+://", "").replaceFirst("/", ":")
                    //sh("git remote set-url origin $repository")
                    sh(returnStdout: true, script: "git tag --points-at HEAD")
                    //sh ("git push -f --tags")
                    sh("git push --all -f origin v0.${env.n}")
                }
                
              }
        }
    }
   def getSum(int counter){
       for (int i=0; i < ${counter}; i++){
         echo i
        }
   }    
}

