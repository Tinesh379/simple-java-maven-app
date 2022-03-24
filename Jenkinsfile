pipeline{
  agent any
  parameters{
    string(name: 'app_version', defaultValue:'1.0-alpha-snapshot', description: 'authored by above user')
  }
  
  stages{
    stage('Deploy to Host'){
      steps{
      sh ' echo "hello world" '
      }
    }
    stage('show pom version'){
      steps{
        getProjectVersion()
      }
    }
  }
}

def getProjectVersion(){
  def pom = readFile 'pom.xml'
  return pom.version
}
