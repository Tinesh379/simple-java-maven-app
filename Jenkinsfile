pipeline{
  
  agent any
  
  parameters{
    string(name: 'app_version', defaultValue: '', description: 'enter version or will take default value of pom')
 }
 
  stages{
  
    stage('Deploy to Host'){
      steps{
      sh ' echo "hello world" '
      }
    }
    
    
    stage('show pom version'){
      steps{
        script{
        def service_version = $app_version.trim() ? $app_version.trim() : getProjectVersion()
        echo " below is the latest pom version"
        echo "${getProjectVersion()}"
        echo " below is the string entered in jenkins"
        echo "$service_version"
        }
      }
    }
  }
}

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}



