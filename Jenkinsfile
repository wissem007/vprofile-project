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
        RELEASE_REPO = 'vprofile-repo'
        CENTRAL_REPO = 'vprofile-central-repo'
        NEXUS_GRP_REPO = 'vprofile-grp-repo'
        NEXUS_IP = '192.168.33.20'
        NEXUS_PORT = '8081'
        NEXUS_LOGIN = "nexuslogin"
    }

    stages{
        stage('BUILD'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo "Archiving the code...."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('TEST'){
            steps {
                sh 'mv -s settings.xml test'
            }
        }
        stage ('CHECKSTYLE ANALYSIS'){
            steps {
                sh 'mvn -s settings.xml checkstyle:checkstyle'
            }
        }

    }
}

