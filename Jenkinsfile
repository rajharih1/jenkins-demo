node {
	def var
	
	stage('Clone repository'){
		/* Clone the repository to our workspace*/
		checkout scm
	}
	
	stage('Build Image'){
	
	var=docker.build("hubrajesh/ngdemo")
	}
	
	stage('Test Image'){
	
	var.inside{
		sh 'echo "Some tests to run"'
		}
	}
	
	stage('Push Image'){
		docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials'){
			var.push("${env.BUILD_NUMBER}")
			var.push("latest")
	
		}

	}
	stage('Deploy image'){
		docker pull hubrajesh/ngdemo
		docker run -itd hubrajesh/("${env.BUILD_NUMBER}")
}