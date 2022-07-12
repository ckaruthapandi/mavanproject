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
	     stage('artifact upload to S3') {
		try {
			sh '''
			cd /home/ubuntu/maven/mavanproject/mavenproject/target/ 
			aws s3 cp s3://karuthapandi/*.war  --region ap-south-1
    			sh "aws s3 ls "
			sh '''
			}	
		    }catch(err) {
			sh "echo error sending to artifact"
			}
	}
}
}
