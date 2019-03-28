
pipeline
{
    agent any
    tools {nodejs "NodeJS"}
    stages{

        stage ('Cloning git'){
            steps{
            git 'https://github.com/rakeshaggarwal1980/AngularAppForDevOps'
            }
        }
        stage ('Install libraries')
        {
            steps{
                dir('WebApp')
                {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('docker build')
        {
            steps{
                dir('WebApp')
                {
                    sh 'docker image build -t my-angular-app .'
                }
            }
            post{
                always{
                sh 'docker image ls'
                sh 'docker run -p 3001:80 --rm my-angular-app'
                }
            }

        }
    }
}