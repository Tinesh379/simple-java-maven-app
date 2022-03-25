pipeline{
  
  agent any
  stages{
   
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
        echo " below is the string entered in jenkins
        }
      }
    }
  }
}

properties(
            [parameters(
              [choice(choices: ['BUILD', 'DEPLOY'], description: 'select build or deploy ', name: 'BUILD_ORDEPLOY'), 
               choice(choices: ['IT', 'UAT', 'PROD'], description: 'choose the environment to deploy ', name: 'ENVIRONMENT'), 
               [$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', description: 'select release version to deploy', filterLength: 1, filterable: false, name: 'SERVICE_VERSION', randomName: 'choice-parameter-5803932932773', 
                script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], 
                script: [classpath: [], sandbox: false, script: 'return[ \'RFC20.16.85\', \'RFC20.16.86\', \'RFC20.16.87\' ]']]], 
               string(defaultValue: '<empty>', description: 'Enter Valid RFC number for Production Deployment', name: 'CHANGE REQUEST', trim: true)])])

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}



