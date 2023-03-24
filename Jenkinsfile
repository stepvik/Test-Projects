pipeline {
    agent 
        {
            label 'linux' 
        }
    
    tools {
        maven '3.8.6'
    }
    
    stages {
        stage ('checkout') {
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage ('build') {
            steps {
                sh "env | sort" 
                sh 'mvn clean install'
            }
        }
        stage ('test') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('only MR') {
            when {
                branch 'MR-*'
            }
            steps {
                sh "env | sort"
            }
        }
    }
}
