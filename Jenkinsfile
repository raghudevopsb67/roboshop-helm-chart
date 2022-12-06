pipeline {
  agent any

  parameters {
    string(name: 'component', defaultValue: '', description: 'Component Name')
    string(name: 'appVersion', defaultValue: '', description: 'Component appVersion')
  }

  stages {

    stage('CheckOut Application Code') {
      steps {
        dir('APP') {
          git branch: 'main', url: "https://github.com/raghudevopsb67/${component}"
        }
      }
    }

    stage('Helm Deploy') {
      steps {
        sh '''
          helm install ${component} . -f APP/helm/prod.yml
        '''
      }
    }


  }

}
