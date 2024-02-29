pipeline {
  agent any
   environment {
        PATH = "/root/.nvm/versions/node/v18.17.1/bin:$PATH"
  }
  stages {
    stage('Build') {
      steps {
        script {
          git branch: 'main', url: 'https://github.com/ursite-io/urpage-core.git'
          sh 'npm install'
          sh 'npm run build'
        }

      }
    }

    stage('Deploy') {
      steps {
        script {
            sshagent(credentials: ['ssh-1']) {
                sh 'ssh ea@192.168.1.200 "pm2 restart urpage"'
            }
        }

      }
    }

  }
}
