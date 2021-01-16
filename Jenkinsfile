pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'python3 App/tests/test.py'
            }
        post {
           success{
               echo "Success"
        }
           failure{
               echo "Failed"
        }
     }
        }
    
    stage('Build') {
        steps{
                sh 'docker build --tag=python-app . '
         }
            }
    stage('Upload'){
        steps{
               withCredentials([usernamePassword(credentialsId: 'docker_id', passwordVariable: 'passwordVariable', usernameVariable: 'usernameVariable')]) {
                  sh 'docker login -u=$usernameVariable -p=$passwordVariable'
                  sh 'docker tag python-app mohamedsalah/python-app'
                  sh "docker push mohamedsalah/python-app:latest"
        }
    } 
        }

     stage('Deploy') {
            steps {
                 withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'AWSCredentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                    sh './infrastructure/create.sh mystack infra/kubernetes_infra.yml infra/params.json'
                }
           }
        }
      
    }
}
