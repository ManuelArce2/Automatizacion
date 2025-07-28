pipeline {
    agent any
    
    triggers {
        githubPush()
    }

    stages{
        stage('Checkout'){
            steps{ git branch: 'main', url: 'https://github.com/ManuelArce2/Automatizacion.git'
            }

            }
            stage('Build'){
                steps{
                    bat 'echo "Hello World bulding the app"'
                }
            }
        }
    }
