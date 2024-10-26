pipeline {
    agent {label 'JDK8'}

    environment {
    MVN = '/opt/apache-maven-3.9.9/bin/mvn'
}

    options {
        timeout(time:1, unit: 'HOURS')
        retry(3)
    }

    triggers {
        cron ('0 * * * *')
    }

    stages {
        stage('clone'){
            steps{
                git url: 'https://github.com/Batman-22/spring-petclinic.git', branch: 'main'
            }
        }
        stage('build'){
            steps{
                sh "$MVN clean package"
            }
        }

        stage('Reporting'){
            steps{
                junit testResults: 'target/surefire-reports/*.xml'
            }
        }
    }
        post {
            success {
                // send the success email.. to be configured
                echo "Success"
            }
        
            unsuccessful {
                // send the failure email.. to be configured
                echo "Failure"
            }
        }
}
