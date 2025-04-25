// pipeline {
//     agent any

//     stages {
//         stage('Checkout Code') {
//             steps {
//                 git branch: 'main', url: 'https://github.com/Aayushi2104/SAPP'
//             }
//         }

//         stage('Build and Run with Docker Compose') {
//             steps {
//                 script {
//                     sh 'docker-compose down'
//                     sh 'docker-compose up --build -d'
//                 }
//             }
//         }

//         stage('Verify Containers') {
//             steps {
//                 sh 'docker ps -a'
//             }
//         }

//         stage('Clean Unused Images') {
//             steps {
//                 sh 'docker image prune -f || true'
//             }
//         }
//     }

//     post {
//         success {
//             echo '✅ Deployment successful!'
//         }
//         failure {
//             echo '❌ Pipeline failed!'
//         }
//     }
// }
pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'youtube-backend'
    }

    // stages {
    //     stage('Clone Repository') {
    //         steps {
    //             git 'https://github.com/Aayushi2104/SAPP.git'
    //         }
    //     }

        stage('Build Docker Images') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Run Containers') {
            steps {
                sh 'docker-compose up -d'
            }
        }

        stage('Check Running Containers') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
