pipeline {
    agent {
        label 'WINDOWS_NODE'
    }
    stages {
        stage('Git Checkout'){
            steps {
                echo "Checking out from Git repo";
                git 'https://github.com/Effiongoto/Pipeline-Script.git'
            }
        }
        stage('Build'){
            steps {
                echo "Building the checked-out project";
                bat 'Build.bat'
            }
        }
        stage('Unit Test'){
            steps {
                echo "Running JUnit test"; 
                bat 'Unit.bat'
            }
        }

        stage('Quality-Gate'){
            steps {
                echo "Verifying Quality Gate";
                bat 'Quality.bat'
            }
        }

        stage('Deploy'){
            steps {
                echo "Deploying Artifact"; 
                bat 'Deploy.bat'
            }
        }
    }

    post {
        always {
            echo "This will always run"
        }
        success {
            echo "This will run only if successful"
        }
        failure {
            echo "This will run only if failed"
        }
        unstable {
            echo "This will run only if the run was marked as unstable"
        }
        changed {
            echo "This will run only if the state of the pipeline has changed"
            echo "For example, if the Pipeline was previously failing but now is successful"
        }
    }
        
}
