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
                script: [classpath: [], sandbox: false, script: 'def choice = getVersionsFromArtifactory() return choice'], 
               string(defaultValue: '<empty>', description: 'Enter Valid RFC number for Production Deployment', name: 'CHANGE REQUEST', trim: true)])])

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}

def getVersionsFromArtifactory(){
  def output = return[ '20.16.85', '20.17.86', '20.18.87', 20.19.87' ]
                      return output.tokenize()
       }



