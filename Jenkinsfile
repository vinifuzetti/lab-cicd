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
    }
	post {
		success {
			githubNotify status: "SUCCESS", 
						 credentialsId: "github", 
						 account: "prof-eduardo-galego", 
						 repo: "lab-cicd",
						 description: "Sucesso"
						 
        }
        failure {
            githubNotify status: "FAILURE", 
						 credentialsId: "github", 
						 account: "prof-eduardo-galego", 
						 repo: "lab-cicd",
						 description: "Erro"
        }
    }
}
