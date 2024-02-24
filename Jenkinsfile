pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          git branch: 'main', url: 'https://github.com/ursite-io/urpage-core.git'
          sh 'export NVM_DIR="$HOME/.nvm"'
          sh '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"'
          sh '[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"'
          sh 'npm install'
          sh 'npm run build'
        }

      }
    }

    stage('Deploy') {
      steps {
        script {
          sh 'pm2 restart app.js --name "tu_app_nextjs"'
        }

      }
    }

  }
}
