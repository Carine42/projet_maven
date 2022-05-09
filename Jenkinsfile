pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction a dÃ©marrÃ©'
        bat 'mvn -B -DskipTests clean package'
        echo 'Construction terminée'
      }
    }

    stage('Test') {
      steps {
        echo 'test va d�marr�'
        bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
      }
    }

  }
}