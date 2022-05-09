pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction a démarré'
        bat 'mvn -B -DskipTests clean package'
      }
    }

  }
}