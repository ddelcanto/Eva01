pipeline {
    agent any

    tools {
        maven 'Maven-Local'   // 💡 Nombre configurado en Manage Jenkins → Tools → Maven
        jdk 'jdk23'           // 💡 Nombre configurado en Manage Jenkins → Tools → JDK
    }

    environment {
        DEPLOY_DIR = '/Users/danieldelcanto/Desktop/deploy' // Carpeta destino del artefacto
    }

    stages {

        stage('Obtener código fuente') {
            steps {
                echo '📥 Clonando repositorio desde GitHub...'
                git branch: 'main', url: 'https://github.com/ddelcanto/Eva01.git'
            }
        }

        stage('Compilar con Maven') {
            steps {
                echo '⚙️ Compilando proyecto con Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Análisis de código') {
            steps {
                echo '🔍 Ejecutando análisis de código (simulado)...'
                sh 'mvn verify'
            }
        }

        stage('Empaquetar artefacto') {
            steps {
                echo '📦 Empaquetando JAR...'
                sh 'mvn package'
            }
        }

        stage('Deployment') {
            steps {
                echo '🚀 Realizando deployment simulado...'
                sh '''
                    mkdir -p "$DEPLOY_DIR"
                    cp target/*.jar "$DEPLOY_DIR" || echo "⚠️ No se encontró el .jar para desplegar."
                    echo "✅ Aplicación desplegada en: $DEPLOY_DIR"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline ejecutado correctamente.'
        }
        failure {
            echo '❌ Hubo un error en alguna etapa del pipeline.'
        }
    }
}
