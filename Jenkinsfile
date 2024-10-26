pipeline {
    agent {label 'JDK8'}

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
                sh 'mvn clean package'
            }
        }

        stage('Reporting'){
            steps{
                junit testResults: 'target/surefire-reports/*.xml'
            }
        }
    }
}
        
    
