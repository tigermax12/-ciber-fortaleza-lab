pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Descarga el código del repositorio configurado en el Job [cite: 27, 35]
                checkout scm
            }
        }
        stage('Test') {
            steps {
                // Instalación de dependencias necesarias en el entorno de Jenkins
                sh 'pip install --break-system-packages pybuilder'
                
                // MODIFICACIÓN CISO: Ejecutar PyBuilder (pyb) en lugar de python test.py 
                // Usamos la ruta absoluta donde se instaló el binario según tus logs
                sh '/var/jenkins_home/.local/bin/pyb'
            }
        }
        stage('Deploy') {
            steps {
                // Limpieza: Detiene y elimina el contenedor si ya existe para evitar conflictos
                sh 'docker rm -f bioguard-container || true'
                
                // MODIFICACIÓN CISO: Despliegue en puerto seguro 8443 en lugar de 5000 [cite: 33, 34]
                // Se usa una imagen genérica de python/flask o la tuya propia
                sh 'docker run -d --name bioguard-container -p 8443:5000 python:3.9-slim'
            }
        }
    }
}
