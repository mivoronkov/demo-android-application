pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: fastlane
            image: softartdev/android-fastlane
            command:
            - cat
            tty: true
        '''
    }
  }
  stages {

    stage('fastlane') {
      steps {
        container('fastlane') {
          sh 'fastlane ${LANE}'	   
				   
        }
      }
    }
  }
  post {
	always {
		archiveArtifacts artifacts: 'app/build/outputs/apk/release/app-release.apk', onlyIfSuccessful: true
	  }
  }
}
