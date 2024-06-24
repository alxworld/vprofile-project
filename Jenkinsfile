pipeline {
    
	agent any

	tools {
        maven "MAVEN3"
        jdk "OracleJdk8"
    }

    environment {
        SNAP_REPO = 'vpr-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'grace098'
        RELEASE_REPO = 'vpr-alex'
        CENTRAL_REPO = 'vpr-maven-central'
        NEXUSIP = '172.31.33.9'
        NEXUSPORT = '8081'
        NEXUS_GRP_REPO = 'vpr-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }
	
    stages{
        
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/*.war'
                }
                failure {
                    echo 'Build Failed'
                }
            }
        }

        stage('Test'){
            steps {
                sh 'mvn -s settings.xml test'
            }
            post {
                success {
                    echo 'Test Passed'
                }
                failure {
                    echo 'Test Failed'
                }
            }
        }

        stage('Checkstyle Analysis'){
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }
            post {
                success {
                    echo 'Checkstyle Passed'
                }
                failure {
                    echo 'Checkstyle Failed'
                }
            }
        }

    }


}
