pipeline {
   agent any
tools {
    maven 'Maven 3.6.0'
    jdk 'java1.8.0'
  }
   stages {
      stage('BUILD') {
           steps {
           
           sh "mvn -B -DskipTests clean package"
         }
        }
        stage('Test'){
        steps {
        sh 'mvn test'
        }
        }
        stage('Deploy') {
           steps {
            sh 'java -jar target/jacoco.exec'
            }
        }

   stage('Artifactory') {
           steps {
           sh 'curl -X PUT -u admin:Javeed@90 -T target/jacoco.exec "http://104.211.223.66:8081/artifactory/example-repo-local/jacoco.exec"'
            }
        }
}

}
