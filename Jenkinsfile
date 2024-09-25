def secret = 'general'
def vmapps = 'alvin@10.148.0.3'
def dir    = '/home/alvin/dumbflix-frontend'
def branch = 'master'

pipeline {
    agent any
    stages {
        stage ("pull") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  cd ${dir}
                  git pull origin ${branch}
                  echo "Git Pull Telah Selesai"
                  exit
                  EOF"""
                }
            }
        }
        stage ("build") {
           steps {
               sshagent([secret]){
                  sh """ssh -o StrictHostKeyChecking=no ${vmapps} << EOF 
                  cd ${dir}
                  npm install
                  echo "installation dependencies telah selesai"
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
                  pm2 start ecosystem.config.js
                  echo "apllication already run"
                  exit
                  EOF"""
                }
            }
        }
    }                           
}
