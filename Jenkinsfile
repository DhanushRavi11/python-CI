pipeline{
	agent any
	stages{
		stage('Git-Checkout'){
			steps{
				git branch: 'S3-file-browser' ,url: "https://github.com/DhanushRavi11/python-CI.git"
			}
		}
		stage('Build-docker-image'){
			steps{
				sh 'docker build -t pythonci:1 .'
			}
		}
		stage('Build-container'){
			steps{
				sh '''
					docker stop python_Con || true
					docker rm python_Con || true
					docker run -it -d --name python_Con -p 8501:8501 pythonci:1
				'''
			}
		}
	}
}
