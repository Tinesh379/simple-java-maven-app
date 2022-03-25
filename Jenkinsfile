pipeline{
  
  agent any
  environment{ 
    DEFAULT_VERSION = "${getProjectVersion()}"
  }
  parameters{
    choice (name: 'BUILD_or_DEPLOY', choices: ['BUILD', 'DEPLOY'], description: 'Pick something')
    string( name: 'App_Version', Description: 'Selelect build no',
       script: [
          $class: 'GroovyScript', 
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
           )
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


