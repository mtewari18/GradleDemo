pipeline {
  agent any
  stages {
    stage ('Build') {
      steps{
        echo 'Running build automation'
                sh './gradlew build --no-daemon'
            }
        }
    stage("Docker build") {
     steps {
      
          sh "docker build -t mtewari18/HWorld ."
          }
    }
    stage("Docker push") {
     steps {
          sh "docker login -u mtewari -p Kanpur@3209"

          sh "docker push mtewari/HWorld"
          }
    }
stage("Deploy to staging") {
     steps {
 
          sh "docker run -d --rm -p 8765:8080 --name HWorld mtewari/HWorld"
     }
}
    }
}
 
