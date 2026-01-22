pipeline {
  agent any
  tools {
    nodejs('20.20.0')
        }
  stages {
      stage ("install dependency stage"){
         steps {
           echo "installing dependencies"
           sh 'npm install'
           }
        }
      stage ("build stage"){
         steps {
           echo "building"
           sh 'npm run build'
           }
        }
      stage ("linting stage"){
         steps {
           echo "linting"
           sh 'npm run lint'
           }
        }
      stage ("test stage"){
         steps {
           echo "testing"
           sh 'npm test'
           }
        }
      stage ("archive stage"){
         steps {
           echo "archiving"
           archiveArtifacts artifacts: "dist/*", fingerprint: true
           }
        }
      stage ("deploy stage"){
         steps {
           echo "deploying"
           sh """
           #!/bin/bash
           cd dist
           sudo cp -rv . /var/www/html
           """
           }
        }
    }	

}
