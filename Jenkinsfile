pipeline{
      agent any
      stages{
          stage ('Upload to AWS') {
             steps {
                  sh 'echo "Hello World from AWS"'
              	
                  withAWS([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AKIAYV4HSDSJD7AAI7EG', region:'us-east-2', credentialsID:'blueocean', secretKeyVariable: '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']]) {
                  sh '''
                        mkdir -p ~/.aws
                        echo "[default]" >~/.aws/credentials
                        echo "[default]" >~/.boto
                        echo "aws_access_key_id = ${AKIAYV4HSDSJD7AAI7EG}" >>~/.boto
                        echo "aws_secret_access_key = ${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}">>/.boto
                        echo "aws_access_key_id = ${AKIAYV4HSDSJD7AAI7EG}" >>~/.aws/credentials
                        echo "aws_secret_access_key = ${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}">>/.aws/credentials
                  
                		echo "Multiline shell steps works too"
                		ls -lah
                        
                    s3Upload(file:'index.html', bucket:'jenkinslakshmibhargaviproject', path:'path/to/target/file.txt')
              	'''
                     
              }
           }
        }
 }       
     
        
