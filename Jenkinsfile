node ('Ubuntu-app-agent'){
	def app
        stage ('Clone from GIT') {
			checkout scm
		}
	stage ('Biuld-and-Tag') {
			app = docker.build("moin4hackdockhub/snake")
		}
        stage ('POST-tO-Dockerhub') {
			docker.withRegistry('https://registry.hub.docker.com', 'moin4hackdockhub'){
				app.push("latest")
			}
	}
	/* stage('Push image') {
           withDockerRegistry([ credentialsId: "moin4hackdockhub", url: "" ]) {
             dockerImage.push()
            }
         }*/
	 stage ('Pull-image-from-docker') {
			sh 'docker-compose down'
		 	sh 'docker-compose up -d'
	}
        
}
