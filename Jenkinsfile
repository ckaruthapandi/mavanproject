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
		sh 'aws s3 cp pom.xml s3://karuthapandi/'
		sh 'aws s3 ls s3://karuthapandi'

		}
            }
	}
}
