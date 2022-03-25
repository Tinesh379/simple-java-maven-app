pipeline{
  
  agent any
  environment{ 
    DEFAULT_VERSION = "${getProjectVersion()}"
  }
  parameters{
    choice (name: 'BUILD_or_DEPLOY', choices: ['BUILD', 'DEPLOY'], description: 'Pick something')
    [$class: 'StringParameter',
       description: 'enter pom version to deploy',
       name: 'app_version',
       defalultValue: 'select Deploy',
       script: [
          $class: 'GroovyScript', 
           fallbackScript: [
               classpath: [], 
               sandbox: false, 
               script: 
                    'return[\'Please select DEPLOY\']'
               ], 
           script: [
                classpath: [], 
                sandbox: false, 
                script: 
                    '''
                    if (params.equals("DEPLOY")){
                                return[${env.DEFAULT_VERSION}]
                            }
                    '''
                ]
            ]
       ]
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


