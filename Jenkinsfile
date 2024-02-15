pipeline {
    agent any
    
    stages{
        stage("clone "){
            steps{
                echo "dipchand yadav "
                git url: "https://github.com/dipchand98/django-notes-app.git",branch: "main"
            }
            
        }
        
        stage("build"){
            steps{
                echo "building a application on into a conatiner "
                sh "docker build -t prem-dip-app ."
                
                }
                
        }
        
        
        stage("push to dockerHub"){
            steps{
                echo "pushing a appliaction into dockerHub"
                withCredentials([usernamePassword(credentialsId:"dockerHub", usernameVariable:"user", passwordVariable:"pass")]){
                sh "docker tag prem-dip-app ${env.user}/prem-dip-app1"
                sh "docker login -u ${env.user} -p ${env.pass}"
                sh "docker push ${env.user}/prem-dip-app1"
                
                
                }
            }
        }
        
        stage("deploy"){
            steps{
                echo "deploying application on ec2 vibe hai aur kya "
                sh "docker-compose down && docker-compose up -d"
                
                
            }
        }
        
    }
    
}
