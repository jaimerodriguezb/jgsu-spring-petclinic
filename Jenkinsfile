pipeline {
    agent any

    triggers {pollSCM('* * * * *')}

    stages {
        // Implicit checkout stage

        stage('Build') {
            steps {
                git branch: 'main', url: 'https://github.com/jaimerodriguezb/jgsu-spring-petclinic.git'
                
                bat '.\\mvnw clean package'

            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/TEST-*.xml'
            archiveArtifacts 'target/*.jar'
        }
    }
}
