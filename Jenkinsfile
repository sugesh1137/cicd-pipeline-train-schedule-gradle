pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                echo "Running the automation!!"
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip' 
            }
        }
        stage('DeploytoStage) {
              steps {
                  withCredentials([usernamePassword(credentialId: 'webserver_user', usernameVariable: 'USERNAME', passwordVariable: "PASSWD")])
                  sshPublisher(
                      publishers: [
                          sshPublisherDesc(
                              configName: 'Stage',
                              sshCredentials: [
                                  username: "$USERNAME",
                                  encryptedPassphrase: "$PASSWD"
                                  ],
                              transfers: [
                                  sshTransfer(
                                      sourceFiles: 'dist/trainScheduler.zip'
                                      removePrefix: 'dist/'
                                      remoteDirectory: '/tmp'
                                      )
                                  ]
                              )
                          ]
                      )
              }                    
    }
}
