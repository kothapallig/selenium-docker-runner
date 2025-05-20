pipeline{
    agent any
    stages {
        stage('Start Selenium Grid') {
            steps {
                sh 'docker-compose -f grid.yml up -d'
            }
        }
        stage('Start Running Test Suite') {
            steps {
                sh 'docker-compose -f test-suite.yml up -d'
            }
            
        }     
        
    }
    post {
        always {
            echo 'Cleaning up...'
            sh 'docker-compose -f grid.yml down'
            sh 'docker-compose -f test-suite.yml down'
        }
    }
}
    