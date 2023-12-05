pipeline {
    agent any

    stages {
        stage('Mostrar ID del Commit') {
            steps {
                script {
                    // Obtener el ID del último commit
                    def commitId = sh(script: 'git rev-parse HEAD', returnStdout: true).trim()
                    echo "ID del último commit: ${commitId}"
                }
            }
        }

        stage('Listar Archivos') {
            steps {
                // Listar los archivos en el directorio del repositorio
                sh 'ls -la'
            }
        }

        stage('Aprobación de Despliegue') {
            steps {
                // Solicitar aprobación manual
                input '¿Aprobar el despliegue a producción?'
            }
        }

        // stage('Despliegue a Producción') {
        //     steps {
        //         // Agregar comandos para desplegar en producción
        //         // Puedes simplemente copiar los archivos a un servidor web, por ejemplo
        //         // Ejemplo: sh 'cp -r * /ruta/del/servidor'
        //     }
        // }

        stage('Notificación de Despliegue') {
            steps {
                // Agregar comandos para notificar sobre el despliegue
                // Puedes incluir el ID del commit en la notificación
                script {
                    echo "Despliegue completado exitosamente para el commit: ${commitId}"
                }
            }
        }
    }
}
