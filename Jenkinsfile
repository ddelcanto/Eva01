pipeline {
    agent any

  tools {
        maven 'Maven-3.9.11'   // 👈 nombre que pusiste en Jenkins
    }

    stages {
        stage('Obtener código fuente') {
            steps {
                git branch: 'main', url: 'https://github.com/ddelcanto/Eva01.git'
            }
        }

        stage('Compilar con Maven') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Análisis de código') {
            steps {
                echo 'Ejecutando análisis de código (simulado)...'
                sh 'mvn verify'
            }
        }

        stage('Deployment') {
            steps {
                echo 'Realizando deployment (simulado)...'
                sh 'echo "Desplegando aplicación en entorno de prueba"'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline ejecutado correctamente!'
        }
        failure {
            echo '❌ Hubo un error en alguna etapa.'
        }
    }
}
