#!Groovy
pipeline {
  agent {
    docker {
       image 'library/composer'
//       args 'composer install'
     }
  }
  stages {
    stage('PHP test') {
      steps {
          sh 'php --version'
      }
    }
    stage('install composer') {
      steps {
        sh 'composer install'
      }
    }
    stage('test phpunit') {
      steps {
        sh './vendor/bin/phpunit --version'
      }
    }
    stage('run phpunit') {
      steps {
        sh './vendor/bin/phpunit --log-junit results/phpunit/phpunit.xml'
      }
    }
  }
  post {
    always {
      junit 'results/**/*.xml'
    }
  }
}
