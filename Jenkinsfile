pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'La construction a dÃƒÂ©marrÃƒÂ©'
        bat 'mvn -B -DskipTests clean package'
        echo 'Construction terminÃ©e'
        archiveArtifacts '**/target/*.jar'
      }
    }

    stage('Test') {
      parallel {
        stage('Unit') {
          steps {
            echo 'test va démarré'
            bat 'mvn -Dtest="com.example.testingweb.smoke.**" test'
            junit '**/target/surefire-reports/TEST-*.xml'
          }
        }

        stage('Integration') {
          steps {
            echo 'Integration commence'
            bat 'mvn -Dtest="com.example.testingweb.integration.**" test'
            echo 'Integration termine'
          }
        }

        stage('Fonctional') {
          steps {
            echo 'Debut fonctionnel'
            bat 'mvn -Dtest="com.example.testingweb.functional.**" test'
            echo 'fin fonctional'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Debut deploy'
        bat 'mvn -B -DskipTests install'
      }
    }

  }
}