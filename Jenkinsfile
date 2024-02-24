pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          git branch: 'main', url: 'https://github.com/ursite-io/urpage-core.git'
          sh 'source /etc/profile'
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
