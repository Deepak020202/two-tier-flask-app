@Library('Shared-Libraries') _

pipeline { 
    agent { label 'linux' }

    stages {
        stage('Code Clone') {
            steps {
                clone("https://github.com/Deepak020202/two-tier-flask-app.git", "master")
            }
        }

        stage('File System Scan') {
            steps {
                trivy()
            }
        }

        stage('Code Build') {
            steps {
                docker_build("flask-app")
            }
        }

        stage('Push to Docker Hub') {
            steps {
                docker_push("DockerHubCreds", "flask-app")
            }
        }

        stage('Code Test') {
            steps {
                echo 'Code is tested'
            }
        }

        stage('Code Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
