pipeline {
    agent any
    environment {
	TRAINING_ID = '801771690413'
	ACCOUNT_ALIAS = 'lunatech-devops-training'
    }
    stages {
        stage('prep') {
            steps {
                cleanWs()
            }
        }
	stage('configure') {
	    steps {
	        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'Lunatech Devops Training credentials']]) {
	            sh("docker pull lunatechlabs/aws-nuke")
    		    sh ("echo $ACCOUNT_ALIAS |docker run -i --mount type=bind,src=$PWD/config/default.yaml,dst=/src/def.yaml ilselott/aws_nuke:latest -c /src/def.yaml --access-key-id $AWS_ACCESS_KEY_ID --secret-access-key $AWS_SECRET_ACCESS_KEY")
		}
	    }
	}
    }
}
