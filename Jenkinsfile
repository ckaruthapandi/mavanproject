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
                    cd /home/ubuntu/maven/mavenproject
                    mvn install
                    '''
                }
            }
        }
}
