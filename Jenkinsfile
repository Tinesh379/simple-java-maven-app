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
  [parameters([choice(choices: ['BUILD', 'DEPLOY'], description: 'Select any option', name: 'BUILD_or_DEPLOY'), 
              choice(choices: ['IT', 'UAT', 'PRODUCTION'], description: 'choose environment to deploy', name: 'ENVIRONMENT'), 
              [$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'SERVICE_VERSION', randomName: 'choice-parameter-408672818199', 
              script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], 
              script: [classpath: [], sandbox: false, script: 'getVersionsFromArtifactory()']]]])])
           

def getProjectVersion(){

 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}

def getVersionsFromArtifactory(){

  def versions =['9848509950','7989718764','9505780585']

  def output = versions.in.text

  return output.tokenize()
}





