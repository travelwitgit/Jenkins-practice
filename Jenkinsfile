
pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
}
}
    stage('Install Python Tools') {
      steps {
        sh '''
           sudo apt-get update
           sudo apt-get install -y python3-pip python3-venv
           '''
}
}

    stage('Check Python') {
       steps {
         sh '''
            python3 --version
            python3 -m pip --version
            '''
}
}
    stage('Install Dependencies') {
      steps {

        sh 'python3 -m venv venv'
        sh 'venv/bin/python -m pip install --upgrade pip'
        sh 'venv/bin/pip install -r requirements.txt'
}
}
    stage('Test') {
      steps {
           sh 'venv/bin/pytest -v'
       }
     }
   }
}

