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
                        docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials') {
                            dockerImage.push('latest')
                        }
                    }
                }
                post {
                    success{
                        echo 'Build and push successful'
                    }
                    failure{
                        echo 'Build and push failed error de creacion de la imagen'
                        mail to: 'jmanuel2101@gmail.com', 
                        from: 'jmanuel2101@gmail.com',
                        subject: "Build and push failed ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: "Build and push failed error de creacion de la imagen ${env.JOB_NAME} #${env.BUILD_NUMBER}"
                    }

                }
            }
        }
    }
