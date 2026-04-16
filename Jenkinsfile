pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Descarga el código de tu repo
                checkout scm
            }
        }
        stage('Test') {
            steps {
                // MODIFICACIÓN: Usamos pyb en lugar de python test.py
                sh 'pip install pybuilder'
                sh 'pyb'
            }
        }
        stage('Deploy') {
            steps {
                // MODIFICACIÓN: Puerto seguro 8443 simulando la nueva política
                // Nota: Asegúrate de que el nombre de la imagen coincida con tu proyecto
                sh 'docker run -d -p 8443:5000 mi-app-bioguard'
            }
        }
    }
}
