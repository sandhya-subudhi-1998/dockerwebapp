node {    
      def app     
      stage('Clone repository') {               
             
            checkout scm    
      }     
      stage('Build image') {         
            
           // docker build -f Dockerfile -t dockerimage .
             docker build -f Dockerfile -t dockerimage .  
       }     
      stage('Test image') {           
            app.inside {            
             
             sh 'echo "Tests passed"'        
            }    
        }     
       stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {            
       app.push("${env.BUILD_NUMBER}")            
       app.push("latest")        
              }    
           }
        }

