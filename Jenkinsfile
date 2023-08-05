pipeline



{

 agent any
   
    
  stages
 
  {
      
       
    stage('ContinuousDownload')
       
        
     {
        
          
        steps
            
           
          {
               
               
           script
               
            {
                   
              try
                   
              {
                      
                git ' https://github.com/intelliqittrainings/maven.git'  
                   
              }
                   
               catch(Exception e1)
                   
                 {
                      
                  mail bcc: '', body: 'jenkins is not download dev code from github', cc: '', from: '', replyTo: '', subject: 'download failed', 

to:'git.admin@gmail.com'
                   
                       
                        exit(1)
}
               
          }
               
            
            
      }

    }
   }
}
