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
                // Instalamos PyBuilder y las dependencias de tu código
                sh 'pip install --break-system-packages pybuilder'
        
                // MODIFICACIÓN CISO: Ejecutar pyb 
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
