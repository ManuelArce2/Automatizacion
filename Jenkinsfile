pipeline {
    agent any
    
    triggers {
        gitlabPush()
    }

    stages{
        stages('checkout'){
            steps{
                git branch: 'main',
                credentialsId: 'gitlab',
                url: 'https://github.com/ManuelArce2/Automatizacion.git'
            }
            stage('build'){
                steps{
                    sh 'echo "Hello World bulding the app"'
                }
            }
        }
    }
}