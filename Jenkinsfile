pipeline {
  agent none
  stages {
    stage('ReadyAPI - Functional') {
      parallel {
        stage('ReadyAPI - Functional') {
          steps {
            echo 'All API Functional tests go here'
          }
        }
        stage('Shopping Cart API Functional tests') {
          steps {
            build(job: 'ReadyAPI Full Stack - Functional', wait: true, quietPeriod: 5)
          }
        }
      }
    }
    stage('ReadyAPI - Performance') {
      parallel {
        stage('ReadyAPI - Performance') {
          steps {
            echo 'All API Performance tests go here'
          }
        }
        stage('Shopping Cart API Performance tests') {
          steps {
            build(job: 'ReadyAPI Full Stack - Performance', wait: true, quietPeriod: 5)
          }
        }
      }
    }
    stage('ReadyAPI - Security') {
      parallel {
        stage('ReadyAPI - Security') {
          steps {
            echo 'All API Securitytests go here'
          }
        }
        stage('Shopping Cart API Security tests') {
          steps {
            build(job: 'ReadyAPI Full Stack - Security', quietPeriod: 5, wait: true)
          }
        }
      }
    }
    stage('ReadyAPI - Virtualization') {
      parallel {
        stage('ReadyAPI - Virtualization') {
          steps {
            echo 'All microservices tests go here.'
          }
        }
        stage('Virtualization - Deploy & Start') {
          steps {
            build(job: 'ReadyAPI Full Stack - Deploy and Start VirtServer', quietPeriod: 5)
          }
        }
        stage('Virtualization - Microservices Tests') {
          steps {
            sleep 10
            build(job: 'ReadyAPI Full Stack - Microservices Test', quietPeriod: 5, wait: true)
          }
        }
        stage('Virtualization - Stop & Undeploy') {
          steps {
            sleep 90
          }
        }
      }
    }
  }
}