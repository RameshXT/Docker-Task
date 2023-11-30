pipeline 
{
    agent any
    stages 
    {
        stage("Clean") 
        {
            steps 
            {
                script 
                {
                    def containers = sh(script: 'docker ps -a -q', returnStdout: true).trim()
                    if (containers) 
                    {
                        sh "docker stop $containers"
                        sh "docker rm $containers"
                    }
                    def images = sh(script: 'docker images -q', returnStdout: true).trim()
                    if (images) 
                    {
                        sh "docker rmi $images"
                    }
                    sh 'sudo rm -rf /var/lib/jenkins/workspace/Docker/*'
                }
            }
        }
        stage("Clone") 
        {
            steps {
                sh 'sudo git clone -b Python https://github.com/RameshXT/Docker-Task.git'
            }
        }
        stage("Build") 
        {
            steps {
                sh 'sudo docker build -t app /var/lib/jenkins/workspace/Docker/Docker-jenkins-tasks'
            }
        }
        stage("Run") 
        {
            steps {
                sh 'sudo docker run -it -d app'
            }
        }
    }
    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
