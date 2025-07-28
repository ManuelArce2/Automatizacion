pipeline {
    agent any
    
    triggers {
        githubPush()
    }
    
    environment{
        DOCKER_IMAGE = 'man2101/automatizacion'
    }

    stages{
        stage('Checkout'){
            steps{ git branch: 'main', url: 'https://github.com/ManuelArce2/Automatizacion.git'
            }

            }
            stage('Build'){
                bat 'echo "%DOCKER_IMAGE%"'
                steps{
                    script{
                        docker.build(DOCKER_IMAGE) 
                        
                    }
                }
            }
        }
    }
