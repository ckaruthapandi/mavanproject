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
		steps {
			aws s3 ls s3://karuthapandi/
}
			}
	}
}
