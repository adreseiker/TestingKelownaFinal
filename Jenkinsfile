pipeline {
    agent any

    environment {
        FIREBASE_TOKEN = credentials('firebase-token')
    }

    stages {
        stage('Test') {
            steps {
                echo 'Manual testing only for this assignment.'
            }
        }

        stage('Staging') {
            steps {
                sh 'firebase deploy --only hosting:staging --token "$FIREBASE_TOKEN"'
            }
        }

        stage('Production') {
            when {
                expression {
                    return env.BRANCH_NAME == 'main' || env.GIT_BRANCH == 'origin/main'
                }
            }
            steps {
                sh 'firebase deploy --only hosting:production --token "$FIREBASE_TOKEN"'
            }
        }
    }
}

//Esteban
