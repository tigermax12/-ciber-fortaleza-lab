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
            // Instalamos PyBuilder
            sh 'pip install --break-system-packages pybuilder'
        
            // MODIFICACIÓN: Usamos la ruta completa del ejecutable
            // El log te indicó que está en /var/jenkins_home/.local/bin/pyb
            sh '/var/jenkins_home/.local/bin/pyb'
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
