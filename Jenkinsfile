pipeline {
  agent any
  stages {
    stage('Prepare') {
      steps {
        sh '''pip install -U platformio
python3 -m platformio update
python3 -m platformio platform install espressif32
python3 -m platformio lib -g install ./'''
      }
    }

    stage('Build examples') {
      steps {
        sh 'python3 -m platformio ci --lib="." --board="esp32dev" ./examples/HAPI-Basic'
      }
    }

    stage('Finalize') {
      steps {
        echo 'Finished'
      }
    }

  }
}