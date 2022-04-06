pipeline{
  
  agent any
  stages{
   
    stage('Hello'){
      steps{
      sh ' echo "hello world" '
      sh 'mvn clover:clover'
      }
    }
    
    stage('Deploy to Host'){
      steps{
        script{
          if (params.ENVIRONMENT.equals('PROD') && params.BUILD_OR_DEPLOY.equals('DEPLOY')){
            println "${params.ENVIRONMENT}"
            println "${params.BUILD_OR_DEPLOY}"
          }
          else{
            echo "you did not select DEPLOY & PROD"
          }
        }
      }
    }
    
    stage('Test options'){
      steps{
        script{
          println " enter CR number is ${listOut()}"
        }
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
    stage('clover report'){
      steps{
        clover (cloverReportFileName: 'clover.xml' , 
                cloverReportDir: 'target/site/clover' ,
                failingTarget: [], 
                healthyTarget: [conditionalCoverage: 80, methodCoverage: 70, statementCoverage: 80], 
                unhealthyTarget: []
               )
      }
    }
    
    stage('list out contents'){
      when{
        branch 'main'
      } 
      steps{
        sh'pwd' 
        sh'ls -altr'
      }
    }
  }
  post{
    success{       
      script{
        if( env.BRANCH_NAME.equals('main')) {
        println "${getProjectVersion()}"
        }
        else{
          println "not master branch"
        }
      }    
    }
  }
  
}

properties([parameters([choice(choices: ['BUILD', 'DEPLOY'], description: 'choose an option', name: 'BUILD_OR_DEPLOY'), 
                        choice(choices: ['IT', 'UAT', 'PROD'], description: 'choose environment to deploy ', name: 'ENVIRONMENT'), 
                        [$class: 'ChoiceParameter', choiceType: 'PT_SINGLE_SELECT', filterLength: 1, filterable: false, name: 'APP_VERSION', randomName: 'choice-parameter-4479796324215', 
                        script: [$class: 'GroovyScript', fallbackScript: [classpath: [], sandbox: false, script: ''], 
                        script: [classpath: [], sandbox: false, script: '''return['v1','v2','v3','v4','v5','v6']''']]], 
              string(defaultValue: '<empty>', description: 'enter valid RFC for production deploy', name: 'CR', trim: true)])])

def getProjectVersion(){

 def pom = readMavenPom file: 'pom.xml'
  return pom.version
}

def listOut(){
  def service = params.CR.trim() ? params.CR.trim() : getProjectVersion()
   return service
  
}







