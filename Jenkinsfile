node {
   def mvnHome
   try{
        GIT_REPO_URL = null
        command = "grep -oP '(?<=projectUrl>)[^<]+' /var/lib/jenkins/jobs/${JOB_NAME}/config.xml"
        GIT_REPO_URL = sh(returnStdout: true, script: command).trim();
        echo "Detected Git Repo URL: ${GIT_REPO_URL}"  
    }
    catch(err){
        throw err
        error "Colud not find any Git repository for the job ${JOB_NAME}"
  }
   stage('Preparation') { 
      // Get some code from a GitHub repository
      sh ' rm -rf ./*'
     git GIT_REPO_URL
   }
   stage('Build') {
        echo sh(returnStdout: true, script: 'env')
        build job: 'test', propagate: true, wait: true,  parameters: [
            string(name: 'APP_NAME', value: JOB_NAME), string(name: 'GIT_REPO_URL', value: GIT_REPO_URL)
        ]
    }
}