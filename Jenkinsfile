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
                        docker.withRegistry('https://index.docker.io/v1/', 'docker-hu') {
                            dockerImage.push('latest')
                        }
                    }
                }
                post {
                    success{
                        echo 'Build and push successful'
                    }
                    failure{
                        echo 'Build and push failed'
                    }

                }
            }
        }
    }
