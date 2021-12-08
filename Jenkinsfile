pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                echo "Running the automation"
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip' 
            }
        }
    }
}
