def secret = 'test'
def vmapps = 'alvin@10.148.0.3'
def dir    = '/home/alvin/dumbflix-frontend'
def branch = 'master'
def images = 'dumbflix-fe'
def tag    = 'latest'

pipeline {
    agent any
    stages {
        stage ("pull") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  echo test
                  exit
                  EOF"""
                }
            }
        }
        stage ("docker build") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  echo test
                  exit
                  EOF"""
                }
            }
        }
        stage ("run") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  echo test
                  exit
                  EOF"""
                }
            }
        }
    }                           
}
