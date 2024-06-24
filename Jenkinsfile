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
        }

    }


}
