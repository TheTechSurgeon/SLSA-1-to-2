pipeline {
    agent {
        docker {
            image 'python:3.9'
        }
    }

    environment {
        DEPENDENCIES_FILE = 'dependencies/requirements.txt'
        BUILD_SCRIPT = 'scripts/build_script.sh'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                sh 'pip install -r ${DEPENDENCIES_FILE}'
            }
        }

        stage('Run Build Script') {
            steps {
                echo 'Running build script...'
                sh 'bash ${BUILD_SCRIPT}'
            }
        }

        stage('Save Logs') {
            steps {
                echo 'Archiving build logs...'
                archiveArtifacts artifacts: 'logs/build_logs/**/*.log', allowEmptyArchive: true
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully.'
        }
        failure {
            echo 'Build failed. Check the logs for details.'
        }
    }
}
