node {
    
    def app

    stage('Clone repository') {
      

      //  git  https://github.com/Alok93singh/kubernetesmanifest.git
        
        
        
        git branch: 'main', url: 'https://github.com/Alok93singh/kubernetesmanifest.git'
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email aloksingh@gmail.com"
                        sh "git config user.name aloksingh"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+BankingApplication.*+BankingApplication:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
