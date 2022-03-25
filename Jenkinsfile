pipeline{
  
  agent any
  
  parameters{
    string(name: 'app_version', defaultValue: '<empty>', description: 'enter version or will take default value of pom')
 }
 
  stages{
    
    stage('Load properties'){
      steps{
        script{
           properties(
                [parameters([[$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'environment', randomName: 'choice-parameter-429424945137', 
                  script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], 
                  script: [classpath: [], sandbox: false, 
                  script: 
                           '''
                           return ['DEV', 'QA', 'PROD']
                           '''
                ]]]])])
        }
      }
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



