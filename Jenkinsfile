pipeline {
    agent any

    stages {
        stage('Build') {
	agent {
                docker { image 'maven:3-alpine' }
            }
            steps {
               sh 'mvn -B -DskipTests clean package'
			   archiveArtifacts 'target/*.jar'
            }
        }
	    stage('Upload') {
		    sh 'echo "***Upload para Nexus***"'
	    }
	    
    }
}
