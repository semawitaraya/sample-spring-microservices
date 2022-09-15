pipeline {
agent {
label 'buildserver'
}

stages {

stage ('Checkout') 
{
steps
    {
    
        checkout scm
        
    }
    
}
stage ('Build') 
{
    steps
    {
       sh "cd /home/semawit/sample-spring-microservices/account-service ; mvn clean install " 
    }
}

   
stage ('dockerimageBuild')
    {
    steps
    {
        sh "cd /home/semawit/sample-spring-microservices/account-service; sudo docker build -t account-service . " 
    }
}
     stage ('dockerimagepush ') 
{
    steps
    {
       sh "cd /home/semawit/sample-spring-microservices/account-service ; sudo  docker login -u938169387 -pnani@2020 "
        sh "cd /home/semawit/sample-spring-microservices/account-service ; sudo docker tag account-service 938169387/spring_microservices "
        sh "cd /home/semawit/sample-spring-microservices/account-service ; sudo docker push 938169387/spring_microservices  "
        
        
    }
}
 stage ('Deploying as a container')
    {
        steps ('deploying'){
            sh "sudo docker run -d --name c23 -p 2222:2222 account-service "
         
        }
        
    }  
   
//stage ('k8sdeployment') 
 //  {
 //     steps {
   //        node (' ansible') {
    //        sh " sudo ansible-playbook /etc/ansible/k8s.yaml"
   
    //}
//}
//}
}
    
 
}
