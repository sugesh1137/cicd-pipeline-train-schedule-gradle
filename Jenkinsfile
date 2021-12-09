pipeline {
    agent any 
    stages {
        stage ('Build') {
            steps{
                echo 'Building with webhook..'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
    }
}
