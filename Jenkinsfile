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

properties([parameters([choice(choices: ['BUILD', 'DEPLOY'], description: 'choose an option', name: 'BUILD_OR_DEPLOY'), 
                        choice(choices: ['IT', 'UAT', 'PROD'], description: 'choose environment to deploy ', name: 'ENVIRONMENT'), 
                        [$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'APP_VERSION', randomName: 'choice-parameter-4479796324215', 
                        script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], 
                        script: [classpath: [], sandbox: false, script: '''def versions = [v1, v2, v3, v4]
def output = versions.in.text
def exitcode= versions.exitValue()
def error = versions.err.text

if (error) {
    println "Std Err: ${error}"
    println "Process exit code: ${exitcode}"
    return exitcode
}
return output.tokenize()''']]], 
              string(defaultValue: '<empty>', description: 'enter valid RFC for production deploy', name: 'CR', trim: true)])])

def getProjectVersion(){

 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}







