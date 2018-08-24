pipeline {
    agent  {
        kubernetes {
            yamlFile './KubernetesPod.yaml'
        }
    }
    environment { 
        // global environment variables.
    }
    stages {
        
        stage('Pre Build Check') {
            environment { 
            }
            steps {
                script {
                    echo "Pre Build staget implement!"
                }
                container('busybox') {
                    sh 'echo Hello Container World in Pre Build Check'
                }
            }
        }
        stage('Build') {
            environment { 
                // Credentials
            }
            steps {
                echo "Build staget implement!"
                container('docker') {
                    sh 'docker version'
                }
            }
        }
        stage('Test') {
            environment { 
                // Environemtn variable for testing.
            }
            steps {
                echo 'Test Stage implement!'
                container('kubectl') {
                    sh 'kubectl version'
                }
            }
        } 
        stage('Deploy') {
            environment { 

            }
            steps {
                echo 'printenv'
                container('helm') {
                    sh 'helm version'
                }
            }
        }
    }
}
