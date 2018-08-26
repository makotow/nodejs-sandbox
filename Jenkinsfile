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
        // stage('Build') {
        //     steps {
        //         echo "Build staget implement!"
        //         container('docker') {
        //             sh 'docker version'
        //         }
        //     }
        // }
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
