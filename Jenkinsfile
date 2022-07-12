pipeline {
     agent {
     label "javajob" }
        stages {
            stage('check out') { 
                steps {
                    git url: 'https://github.com/TechPrimers/jenkins-example'
                }
            }
             stage('build') { 
                steps {
                    sh '''
                    cd /home/ubuntu/maven/mavanproject/mavenproject
                    mvn install
                    '''
                }
            }
	     stage('artifact') {
		steps {
		   sh '''
			withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {
}	
}
}
 stage('Upload to AWS') {
              steps {
                  withAWS(region:'ap-south-1',credentials:'wach-jenkins-cred') {
                  sh 'echo "Uploading content with AWS creds"'
		   cd /home/ubuntu/maven/mavanproject/mavenproject/target                     
		   s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'*.war', bucket:'karuthapandi')
                  }
              }
}
}
