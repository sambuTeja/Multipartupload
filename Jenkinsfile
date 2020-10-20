pipeline {
    agent any 
    stages {
        stage('Clone') { 
            steps {
                sh 'git clone https://github.com/sambuTeja/Multipartupload.git'
            }
        }
        stage('Test') { 
            steps {
                sh '/usr/local/bin/cfn-lint /home/ubuntu/*.json'
            }
        }
        stage('s3upload') { 
            steps {
                sh '/usr/local/bin/aws s3 cp /home/ubuntu/simples3bucket.json s3://tejammed/simples3bucket.json'
            }
        }
        stage('Deploy') { 
            steps {
                sh 'cd /usr/local/bin/'
                sh 'ls'
                sh "/usr/local/bin/aws cloudformation create-stack --stack-name s3bucket --template-body file://simples3bucket.json --region 'eu-west-3'"
            }
        }
    }
}
