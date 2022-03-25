pipeline{
  
  agent any
  
  parameters{
    string(name: 'app_version', defaultValue: '<empty>', description: 'enter version or will take default value of pom')
    choice(name: 'environment', script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], script: [classpath: [], sandbox: false, script: '''return[
\'Europe\',
\'Poland,
\'India
]''']]]])]))
 }

    stage('Deploy to Host'){
      steps{
      sh ' echo "hello world" '
      }
    }
    
    
    stage('show pom version'){
      steps{
        script{
        echo " below is the latest pom version"
        echo "${getProjectVersion()}"
        echo " below is the string entered in jenkins"
        echo "$app_version"
        }
      }
    }
  }
}

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}



