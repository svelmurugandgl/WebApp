pipeline {
  agent any
  stages {
    stage('Dev Code Pull ') {
      steps {
        echo 'Pull the DEV Code'
      }
    }

    stage('Dev Maven Build') {
      steps {
        echo 'Build the Dev Code'
      }
    }

    stage('QA Deploy') {
      steps {
        echo 'Deploy in QA Environment'
      }
    }

    stage('QA Tests') {
      parallel {
        stage('QA Tests') {
          steps {
            echo 'Start QA Test'
          }
        }

        stage('WebUI Test') {
          steps {
            echo 'Start Web UI Test'
          }
        }

        stage('WebAPI Test') {
          steps {
            echo 'Start Web API Test'
          }
        }

      }
    }

    stage('QA Certification') {
      steps {
        input 'Manual Approval'
      }
    }

    stage('UAT Deploy') {
      when {
        not {
          branch 'master'
        }

      }
      steps {
        echo 'Deploy into UAT'
      }
    }

    stage('UAT Certification ') {
      when {
        not {
          branch 'master'
        }

      }
      steps {
        echo 'UAT Certification'
        input 'UAT Approval'
      }
    }

    stage('Prod Deploy') {
      when {
        not {
          branch 'master'
        }

      }
      steps {
        echo 'Production Deploy'
      }
    }

  }
}