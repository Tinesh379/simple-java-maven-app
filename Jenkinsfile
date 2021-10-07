pipeline {
  agent {
    node {
      label 'buildfarm'
    }

  }
  stages {
    stage('download code') {
      parallel {
        stage('download code') {
          steps {
            git(url: 'https://github.com/Tinesh379/simple-java-maven-app.git', branch: 'master')
            echo 'cloned repo from git'
          }
        }

        stage('') {
          agent {
            node {
              label 'buildfarm'
            }

          }
          steps {
            echo 'Hello world'
          }
        }

      }
    }

  }
}