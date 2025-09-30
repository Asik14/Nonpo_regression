pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'       // must match the Name from Jenkins
        maven 'MAVEN_HOME'    // must match the Name from Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Asik14/Nonpo_regression.git'
            }
        }

        stage('Run Single Test Class') {
            steps {
                bat "mvn clean test -Dtest=Nonpo_Process_BranchFlow1"
                junit '**/target/surefire-reports/*.xml' // Publish test reports
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            cleanWs()
        }

        success {
            echo "Pipeline succeeded! 🎉
        }

        failure {
            echo "Pipeline failed! ❌"
        }
    }
}
