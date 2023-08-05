pipeline
{agent any
 stages
 {
  stage('ContinuousDownload')
   {
    steps
     {
      script
        {
           try{
                      
                git ' https://github.com/intelliqittrainings/maven.git'  
               }
               catch(Exception e1)
              {
            mail bcc: '', body: 'jenkins is not download dev code from github', cc: '', from: '', replyTo: '', subject: 'download failed', 

to:'git.admin@gmail.com'
         exit(1)}
         }
      }
   }
  stage('ContinuousBuild')
  { steps
   {
    script
    {
       try
        {
        sh 'mvn package'    
         }
      catch(Exception e2)
        {
                       
              mail bcc: '', body: 'jenkins is  unable to create the artifact from dev code', cc: '', from: '', replyTo: '', subject: 'build failed', to: 'dev.admin@gmail.com'
             exit(1)
        }
   }
   }
  }    
  stage('ContinuousDeploy')
    {
      steps
    {
        script
        
           {
            
              try
            
              {
               
                deploy adapters: [tomcat9(credentialsId: 'd8853d44-8807-4b2c-975d-b90c7c6d2798', path: '', url: 'http://172.31.5.105:8080')], contextPath: 'testapp', war: '**/*.war'  
           
               }
             
              catch(Exception e3)
             
              {
                 mail bcc: '', body: 'jenkins is  unable to create the artifact into tomcat on qaserver', cc: '', from: '', replyTo: '', subject: 'deployment failed', to: 'middleware.team@gmail.com'
                
                 exit(1)
             
              }
       
          }
           
      }
      }
  stage('ContinuousTesting')
 {
      steps
     {
        script
        {
            try
                 
            {
                   
              git ' https://github.com/intelliqittrainings/FunctionalTesting.git'
             
                  
               sh 'java -jar /var/lib/jenkins/workspace/Declarativescriptpipeline/testing.jar'
                 
           }
                 
            catch(Exception e4)
                
           {
                  mail bcc: '', body: 'selenium scripts not executed', cc: '', from: '', replyTo: '', subject: 'testing failed', to: 'qa.team@gmail.com'   
                    
             exit(1)
                 
            }
             
         }
     }
  }
 stage('ContinuousDelivary')
  { steps
            
   {
      script
              
        {
                  
           try
                  
           {
                    
                deploy adapters: [tomcat9(credentialsId: 'd8853d44-8807-4b2c-975d-b90c7c6d2798', path: '', url: 'http://172.31.7.119:8080')], contextPath: 'prodapp', war: '**/*.war'
      
                 
          }
                  
          catch(Exception e5)
                  
          {
                      
            mail bcc: '', body: 'jenkins unable  to deploy into tomcat on prodserver', cc: '', from: '', replyTo: '', subject: 'delivary failed ', to: 'dm.team@gmail.com'
                    
          exit(1)  
                  
          }
         }
             
       }
     }
     }
  }
         
     

   
