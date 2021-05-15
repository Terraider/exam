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
                        dir('')
                        sh 'docker build -t $work $registry:$BUILD_NUMBER .'
                    }
                }
            stage("docker push") {
                steps {
                    dir ('dockers'){
                    git tag -a $BUILD_NUMBER -m "$registry"
                    sh 'docker push $work $registry:$BUILD_NUMBER'
                }
            }
        }
    }
}
