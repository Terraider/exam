 pipeline {
    environment
        {
            gitt=''
        }
    agent{ 
            label 'master'
        }
    stages {
            stage('Cloning our Git') { 
               steps{
                   // клонируем репозиторий на котором лежит всё нужное.
                    git 'https://github.com/Terraider/exam.git'
                    }
                }
            stage("create docker image") {
                steps{
                        // выводим тег из текущей ветки и переводим в переменную.
                        gitt = git 'describe --abbrev=0 --tags'
                        // создаем контейнер с тегом ветки, который мы получили только что.
                        sh 'docker build -t $gitt .'
                    }
                }
            stage("docker push") {
                steps {
                    dir ('dockers'){
                        // переходим в папку (dokers), и кладём туда наш контейнер.
                        sh 'docker push $gitt'
                }
            }
        }
    }
}
