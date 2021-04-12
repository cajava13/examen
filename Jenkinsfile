pipeline {
	agent any	
    stages {
        stage('Source') {
            steps {
				script {
				git 'https://github.com/CharlesPikachu/Games/'					
				}
			}
		}
		stage('Check Folder') {
			when { expression { return fileExists ('/var/jenkins_home/workspace/examenJenkins/Game7') } }
				steps {
					echo "folder exists"									
			    }
	      }
		stage('Rename folder') {
			steps {						
					dir('/var/jenkins_home/workspace/examenJenkins'){
						sh 'ls -ltr /var/jenkins_home/workspace/examenJenkins'	
						sh 'mv /var/jenkins_home/workspace/examenJenkins/Game7 /var/jenkins_home/workspace/examenJenkins/Dino_DevOps'
					
						}			
						
				  }
			  }
		stage('Zip folder') {
			steps{
             	echo 'zip'
					dir('/var/jenkins_home/workspace/examenJenkins'){
					    sh 'zip -r Dino_DevOps.zip /var/jenkins_home/workspace/examenJenkins/Dino_DevOps'
					}
             
          }
	   }
	   stage('Push zip') {
			steps{
             	echo 'Push'
					dir('/var/jenkins_home/workspace/'){
					   //sh 'touch b'
					   sh 'git init'
					   sh 'git add /var/jenkins_home/workspace/examenJenkins/Dino_DevOps.zip'
					   sh 'git commit -m "añadir archivo a repositorio"'
					   sh 'git remote set-url origin git@github.com:cajava13/examen.git'
					   sh 'git push -u -f origin main'					
				echo 'End Push'

					}
             
          }
	   }	      
	   //
	}
		
    post {
       success {
                    echo 'successful'
					mail to: 'carlosfernandezarg@gmail.com',
					subject: "Test DevOps",
                    body: "https://github.com/cajava13/groovy"
               }
         }
    }
	