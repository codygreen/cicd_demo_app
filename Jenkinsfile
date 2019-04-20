node {
   def mvnHome
   stage('Preparation') { 
      // Get some code from a GitHub repository
      //git 'https://github.com/jglick/simple-maven-project-with-tests.git'
      echo GIT_SERVER
   }
   stage('Build') {
        echo sh(returnStdout: true, script: 'env')
        /*build job: 'test', propagate: true, wait: true,  parameters: [
            string(name: 'name', value: "DemoApp"), string(name: 'GIT_SERVER', value: GET_SERVER)
        ]*/
    }
}