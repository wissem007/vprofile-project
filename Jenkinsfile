pipeline {

    agent any

	tools {
        maven "maven3"
	    jdk "OracleJDK8"
    }

     environment {
        NEXUS_USER = 'admin'
        NEXUS_PASSWORD = 'admin'
        SNAP_REPO = 'vprofile-snapshot'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUS_GRP_REPO = 'vpro-maven-central'
        NEXUS_IP = '192.168.33.20'
        NEXUS_PORT = '8081'
        NEXUS_LOGIN = "nexuslogin"
    }

    stages{
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        }
    }
}

