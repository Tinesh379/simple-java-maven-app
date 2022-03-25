pipeline{
  agent any
  environment{
    DEFAULT_VERSION = "${getProjectVersion()}"
  }
  parameters{
    string(name: 'app_version', defaultValue:"${env.DEFAULT_VERSION}", description: 'authored by above user', trim: true)
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
      echo "${env.DEFAULT_VERSION}"
        echo " below is the string entered in jenkins"
        echo "$app_version"
      }
    }
  }
}

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  string POM_VERSION = pom.version 
  return POM_VERSION

}

