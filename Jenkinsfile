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
		sh '''
		cd /home/ubuntu/maven/mavanproject/mavenproject/target/
		aws s3 cp *.war s3://karuthapandi/
		aws s3 ls s3://karuthapandi
		'''
		}
            }
	}
}
