pipeline {
    agent any

    stages {
        stage('Instalar dependencias') {
            steps {
                bat '''
                    REM Crear entorno virtual
                    "C:\\Users\\HP\\AppData\\Local\\Programs\\Python\\Launcher\\py.exe" -m venv venv

                    REM Activar entorno virtual
                    call venv\\Scripts\\activate

                    REM Instalar dependencias (si existe el archivo)
                    if exist requirements.txt (
                        py -m pip install -r requirements.txt
                    ) else (
                        echo "No hay archivo requirements.txt"
                    )
                '''
            }
        }

        stage('Ejecutar pruebas') {
            steps {
                bat '''
                    REM Activar entorno virtual
                    call venv\\Scripts\\activate

                    REM Ejecutar pruebas
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
