def secret = 'general'
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
                  cd ${dir}
                  git pull origin ${branch}
                  exit
                  EOF"""
                }
            }
        }
        stage ("docker build") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  cd ${dir}
                  docker build -t ${images}:${tag} .
                  exit
                  EOF"""
                }
            }
        }
        stage ("run") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  cd ${dir}
                  docker compose up -d
                  exit
                  EOF"""
                }
            }
        }
    }                           
}