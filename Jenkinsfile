pipeline {
    environment
        {
            registry='Exam/dokers'
            work='exam'
        }
    agent { 
            label 'master'
        }
    stages {
            stage('Cloning our Git') { 
               steps {
                    git 'https://github.com/Terraider/exam.git'
                    }
                }
            stage("create docker image") {
                steps {
                        sh 'docker build -t $registry:$BUILD_NUMBER .'
                    }
                }
            stage("docker push") {
                steps {
                    dir ('dockers'){
                        git 'describe'
                        sh 'docker push $work $registry:$BUILD_NUMBER'
                }
            }
        }
    }
}
