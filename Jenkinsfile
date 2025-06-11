pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
        CUSTOM_BIN = "${env.HOME}/bin"
        PATH = "${env.HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'Github',
                    url: 'https://github.com/prashant-aggarwal/awr-devops-eks-cluster.git'
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

        stage('Install eksctl') {
            steps {
                sh '''
                echo "Installing eksctl..."
                export ARCH=amd64
                export PLATFORM=$(uname -s)_$ARCH
                curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"
                tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp
                mkdir -p $HOME/bin
                mv /tmp/eksctl $HOME/bin/eksctl
                chmod +x $HOME/bin/eksctl
                export PATH=$HOME/bin:$PATH
                eksctl version
                '''
            }
        }


    }

    post {
        always {
            cleanWs()
        }
    }
}
