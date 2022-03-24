pipeline{
  agent any
  environments{
    defaultAppVersion = getProjectVersion()
  }
  parameters{
    string(name: 'app_version', defaultValue: '1.0-Snapshot', description: 'authored by above user')
  }
  
  stages{
    stage('Deploy to Host'){
      steps{
      sh ' echo "hello world" '
      }
    }
    stage('show pom version'){
      steps{
        getProjectVersion()
        echo "${env.defaultAppVersion}"
      }
    }
  }
}

def getProjectVersion(){
  def pom = readMavenPom File: 'pom.xml'
  return pom.version
}
