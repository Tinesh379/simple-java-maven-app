pipeline{
  agent any
  environment{
    defaultAppVersion = getProjectVersion()
  }
  parameters{
    string(name: 'app_version', defaultValue:'${pom.version}', description: 'authored by above user')
  }
  
  stages{
    stage('Deploy to Host'){
      steps{
      sh ' echo "hello world" '
      }
    }
    stage('show pom version'){
      steps{
        echo " below is the latest pom version"
        echo "${env.defaultAppVersion}"
      }
    }
  }
}

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}

