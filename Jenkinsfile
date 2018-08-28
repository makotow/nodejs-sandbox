pipeline {
    agent {
        kubernetes {
          label 'jenkins-ci'
          defaultContainer 'jnlp'
          yamlFile 'KubernetesPod.yaml'
        }
    }

    stages {
        
        stage('Pre Build Check') {
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
            steps {
                echo "Build staget implement!"
            
                docker.build("nodejs-build-${env.BUILD_ID}", "-f Dockerfile .").inside() {
                    node -v
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Test Stage implement!'
                container('kubectl') {
                    sh 'kubectl version'
                }
            }
        } 

        stage('Deploy') {
            steps {
                echo 'printenv'
                container('helm') {
                    sh 'helm version'
                }
            }
        }
    }
}
