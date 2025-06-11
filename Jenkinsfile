pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1' // Adjust as needed
        PATH = "${env.HOME}/bin:${env.PATH}" // Include custom kubectl path
    }

	
    stages {
        stage('Checkout Repo') {
			steps {
				git branch: 'main', 
					credentialsId: 'Github', 
					url: 'https://github.com/prashant-aggarwal/awr-devops-eks-cluster.git'
				}
			}
		}

	stage('Install kubectl') {
		steps {
			sh '''
			echo "Installing kubectl..."
			curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.31.2/2024-11-15/bin/linux/amd64/kubectl
			chmod +x ./kubectl
			mkdir -p $HOME/bin
			cp ./kubectl $HOME/bin/kubectl
			export PATH=$HOME/bin:$PATH
			kubectl version --client
			'''
		}
	}
}