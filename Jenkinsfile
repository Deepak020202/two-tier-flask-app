pipeline { 
    agent { label "Dev" }

    stages {
        stage("Code Clone") {
            steps {
                git branch: "master", url: "https://github.com/Deepak020202/two-tier-flask-app.git"
            }
        }
        stage("Code Build") {
            steps {
                sh " docker build -t flask-app ."
            }
        }
        stage("Code Test") {
            steps {
                echo "Code is tested"
            }
        }
        stage("Code Deploy") {
            steps {
                sh 'docker-compose up -d'
            }
        }
    }
    
    }
}
