pipeline {
    agent any

    stages {
        stage('Instalar dependencias') {
            steps {
                bat '''
                    REM Crear entorno virtual
                    "C:\Program Files\Python314\\python.exe" -m venv venv

                    REM Activar entorno virtual
                    call venv\\Scripts\\activate

                    REM Instalar dependencias
                    if exist requirements.txt (
                        "C:\Program Files\Python314\\python.exe" -m pip install -r requirements.txt
                    ) else (
                        echo "No hay archivo requirements.txt"
                    )
                '''
            }
        }

        stage('Ejecutar pruebas') {
            steps {
                bat '''
                    call venv\\Scripts\\activate
                    python test_main.py
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline ejecutado correctamente.'
        }
        failure {
            echo 'Ocurrió un error en la ejecución del pipeline.'
        }
    }
}
