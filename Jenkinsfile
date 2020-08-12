pipeline{
      agent any
      stages{
            stage ('Lint HTML'){
                  steps {
                        //do linting
                  }     
            }
                  
          stage ('Upload to AWS') {
             steps {
                  sh 'echo "Hello World from AWS"'
              	
                  withAWS([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', region:'us-east-2', credentialsID:'blueocean', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                  sh '''
                        mkdir -p ~/.aws
                        echo "[default]" >~/.aws/credentials
                        echo "[default]" >~/.boto
                        echo "aws_access_key_id = ${AWS_ACCESS_KEY_ID}" >>~/.boto
                        echo "aws_secret_access_key = ${AWS_SECRET_ACCESS_KEY}">>/.boto
                        echo "aws_access_key_id = ${AWS_ACCESS_KEY_ID}" >>~/.aws/credentials
                        echo "aws_secret_access_key = ${AWS_SECRET_ACCESS_KEY}">>/.aws/credentials
                  
                		echo "Multiline shell steps works too"
                		ls -lah
                        
                    s3Upload(file:'index.html', bucket:'jenkinslakshmibhargaviproject', path:'C:\Users\teja1\Documents\GitHub\static\index.html')
              	'''
                     
              }
           }
        }
 }       
     
        
