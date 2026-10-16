pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Récupère le code source depuis le dépôt Git configuré dans le job
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Installe les dépendances et prépare un artefact
                sh 'npm install'
                sh 'mkdir -p dist'
                sh 'tar -czf dist/build.tar.gz package.json'
            }
        }

        stage('Test') {
            steps {
                // Exécute les tests unitaires
                sh 'npm test'
            }
        }

        stage('Archive') {
            steps {
                // Archive l'artefact généré
                archiveArtifacts artifacts: 'dist/*.tar.gz', allowEmptyArchive: true
            }
        }
    }
}
