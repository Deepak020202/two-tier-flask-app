pipeline { 
    agent { label "linux" }
    
    stages {
        stage("Code Clone") {
            steps {
                git branch: "master", url: "https://github.com/Deepak020202/two-tier-flask-app.git"
            }
        }
        stages {
        stage("File System Scan ") {
            steps {
                sh "trivy fs . -o Image_Result.json"
            }
        }

        stage("Code Build") {
            steps {
                sh "docker build -t flask-app ."
            }
        }

        stage("Push to Docker Hub") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: "DockerHubCreds",
                    usernameVariable: "DockerHubUser",
                    passwordVariable: "DockerHubPass"
                    )]){
                        sh "docker login -u ${env.DockerHubUser} -p ${env.DockerHubPass}"
                        sh "docker image tag flask-app ${env.DockerHubUser}/flask-app"
                        sh "docker push ${env.DockerHubUser}/flask-app:latest"
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
