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
                steps{
                    script{
                        dockerImage = docker.build(DOCKER_IMAGE) 
                        
                    }
                }
            }
            stage('Push'){
                steps{
                    script{
                        docker.withRegistry('https://hub.docker.com', 'docker-hub-credentials') {
                            dockerImage.push('latest')
                        }
                    }
                }
            }
        }
    }
