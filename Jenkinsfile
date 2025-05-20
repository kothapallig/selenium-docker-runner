pipeline{
    agent any
    stages {
        stage('Start Selenium Grid') {
            steps {
                sh 'docker-compose -f grid.yaml down --remove-orphans'
                sh 'docker-compose -f grid.yaml up -d'
            }
        }
        stage('Start Running Test Suite') {
            steps {
                sh 'docker-compose -f test-suites.yaml down --remove-orphans'
                sh 'docker-compose -f test-suites.yaml up -d'
            }
            
        }     
        
    }
    post {
        always {
            echo 'Cleaning up...'
            sh 'docker-compose -f grid.yaml down'
            sh 'docker-compose -f test-suites.yaml down'
            archiveArtifacts artifacts: 'output/flight-portal/emailable-report.html', fingerprint: true
        }
    }
}
    