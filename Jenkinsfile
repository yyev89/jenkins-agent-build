pipeline {
    agent {
        label 'centos-agent'
    }
    stages {
        stage('Update') {
            steps {
                // update software from repos
                sh "sudo dnf update"
            }
        }
        stage('Install') {
            steps {
                // install apache web server
                sh "sudo dnf install httpd -y"
            }
        }
        stage('Test') {
            steps {
                // test connection to apache
                sh "service httpd status"
            }
        }
        stage('Running script') {
            steps {
                // run bash script for checking 4xx and 5xx status codes in error log
                sh "chmod +x check-codes-apachelog"
                sh "./check-codes-apachelog"
            }
        }
    }
}
