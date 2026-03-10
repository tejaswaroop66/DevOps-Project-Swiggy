pipeline {
    agent any

    tools {
        nodejs "node18"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/tejaswaroop66/DevOps-Project-Swiggy.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Application') {
            steps {
               sh 'CI=false npm run build'
            }
        }
        

        // stage('SonarQube Scan') {
        //     steps {
        //         withSonarQubeEnv('sonar') {
        //             sh 'sonar-scanner'
        //         }
        //     }
        // }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t swiggy-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 3002:3000 swiggy-app'
            }
        }

    }
}
