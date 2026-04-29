pipeline {
    agent any
    stages {
        stage('getcode') {
            steps {
                git branch: 'main', url: 'https://github.com/Yashu-sudo/jenkins-practise.git'
            }
        }
        stage('craeteimae') {
            steps {
                sh 'docker build -t yashu565656/indexpage:new1 .'
            }
        }
        stage('docker login'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'PASS', usernameVariable: 'USER')])
                {sh 'echo $PASS | docker login -u $USER --password-stdin'}
                }
            }
            stage('dockerpush'){
                steps {
                    sh 'docker push yashu565656/indexpage:new1'
                }
            }
            stage('docker cony'){
                steps {
                    sh 'docker run -td --name cont2 -p 1212:80 yashu565656/indexpage:new1'
                }
            }
        }
    }
