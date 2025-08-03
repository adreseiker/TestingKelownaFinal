pipeline {
    agent any
       //Esteban Poblano Romero
    environment {
        FIREBASE_TOKEN = credentials('FIREBASE_TOKEN')
    }

    stages {
        stage('Test') {
            steps {
                echo 'Manual testing only for this assignment.'
            }
        }

        stage('Staging') {
            steps {
                sh 'firebase use staging --token "$FIREBASE_TOKEN"'
                sh 'firebase deploy --only hosting --token "$FIREBASE_TOKEN"'
            }
        }

        stage('Production') {
            when {
                branch 'main'
            }
            steps {
                sh 'firebase use production --token "$FIREBASE_TOKEN"'
                sh 'firebase deploy --only hosting --token "$FIREBASE_TOKEN"'
            }
        }
    }
}
