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

properties([parameters([choice(choices: ['BUILD', 'DEPLOY'], description: 'Select any option', name: 'BUILD_or_DEPLOY'), 
                        choice(choices: ['IT', 'UAT', 'PRODUCTION'], description: 'choose environment to deploy', name: 'ENVIRONMENT'), 
                        [$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'SERVICE_VERSION', randomName: 'choice-parameter-408672818199', 
                         script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], 
                         script: [classpath: [], sandbox: false, script: 'return[ \'IRIS R11.03.00\', \'Legacy R02.03.00\', \'PATHways R02.03.00\' ]']]]])])
           

def getProjectVersion(){
 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}

def getVersionsFromArtifactory(){
  def output = return[ '20.16.85', '20.17.86', '20.18.87', 20.19.87' ]
                      return output.tokenize()
       }



