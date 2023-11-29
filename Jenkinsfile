pipeline
{
    agent any
    stages
    {
        stage( "Clone" )
        {
            steps
            {
                sh ' rm -rf * '
                sh ' git clone https://github.com/RameshXT/Docker-jenkins-tasks.git -b Docker '
            }
        }
        stage( "Build" )
        {
            steps
            {
                sh ' docker build -t jen . '
            }
        }
        stage( "Run" )
        {
            steps
            {
                sh ' docker run -it --name rubyscontainer jen '
            }
        }
    }
}
