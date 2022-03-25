pipeline{
  
  agent any
  environment{ 
    DEFAULT_VERSION = "${getProjectVersion()}"
  }
  parameters{
    string(name: 'app_version', defaultValue: "${env.DEFAULT_VERSION}", description: 'enter version')
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
        echo "${getProjectVersion()}"
        echo " below is the string entered in jenkins"
        echo "$app_version"
      }
    }
  }
}

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}


