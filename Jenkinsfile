pipeline { 
    agent { label "linux" }

    stages {
        stage("Code Clone") {
            steps {
                script {
                    clone("https://github.com/Deepak020202/two-tier-flask-app.git", "master")
                }
            }
        }

        stage("File System Scan") {
            steps {
                script {
                    trivy_fs()
                }
            }
        }

        stage("Code Build") {
            steps {
                script {
                    sh "docker build -t flask-app ."
                }
            }
        }

        stage("Push to Docker Hub") {
            steps {
                script {
                    docker_push("DockerHubCreds", "flask-app")
                }  
            }
        }

        stage("Code Test") {
            steps {
                echo "code is tested"
            }
        }

        stage("Code Deploy") {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
}
