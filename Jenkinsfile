pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Use Maven to build
                echo 'Building...'
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
                sh 'mvn sonar:sonar'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                sh 'mvn verify'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                sh 'deploy-staging.sh'  // Example script
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Testing in staging...'
                sh 'test-staging.sh'  // Example script
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                sh 'deploy-production.sh'  // Example script
            }
        }
    }
    post {
        always {
            mail to: 'kanad72@gmail.com',
                 subject: "Build ${currentBuild.fullDisplayName}",
                 body: "Pipeline completed. Check the results."
        }
    }
}
