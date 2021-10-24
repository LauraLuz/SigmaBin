//Inicio Pipeline Declarativa
pipeline {
  //Utilizar ambiente disponivel
  agent any 
  stages {
    //Etapa de compliar codigo X
    stage('compile') {
      steps {
        bash 'mvn clean install'
      }
    }
    //Etapa de compliar codigo X
    stage('archive') {
      steps {
        parallel(
          "Junit": {
            junit 'target/surefire-reports/*.xml'
          },
          "Archive": {
            archiveArtifacts(artifacts: 'target/Nadia.jar', onlyIfSuccessful: true, fingerprint: true)
            archiveArtifacts(artifacts: 'target/Nadia*javadoc.jar', fingerprint: true)
          }
        )
      }
    }
  }
}
