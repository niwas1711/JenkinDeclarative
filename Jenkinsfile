pipeline {
    agent {
        kubernetes {
            label 'fmwk8s-test-infra-slave'
            namespace 'default'
            inheritFrom 'fmwk8s-test-infra-slave'
        }
    }
    environment{
	  HTTP_PROXY="http://www-proxy-brmdc.us.oracle.com:80"
          https_proxy="https://www-proxy-brmdc.us.oracle.com:80"
          http_proxy="http://www-proxy-brmdc.us.oracle.com:80"
          no_proxy=".us.oracle.com,.oraclecorp.com,.oraclevcn.com"
          NO_PROXY=".us.oracle.com,.oraclecorp.com,.oraclevcn.com"
          HTTPS_PROXY="https://www-proxy-brmdc.us.oracle.com:80"
	 JAVA_HOME="/scratch/syseng/installs/jdk1.8.0"
         M2_HOME="/scratch/syseng/installs/maven"
         M2="/scratch/syseng/installs/maven/bin"
         PATH="$JAVA_HOME:$M2:$PATH"
    }
    
    stages {
        stage('Welcome') {
            steps {
                echo 'Welcome to first declarative stage'
            }
        }
        stage('Git checkout') {
            steps {
                echo 'Welcome Git Checkout stage'
              git branch: 'main', url: 'https://github.com/niwas1711/JenkinDeclarative.git'
            }
        }
        stage('Maven Build') {
            steps {
                echo "Java home ${JAVA_HOME}"
                   echo "Maven home ${M2_HOME}"
                   echo "Maven home ${PATH}"
                sh "mvn clean package"  
            }
        }
      /*  stage('docker Build') {
                    steps {
                        echo "Java home ${JAVA_HOME}"
                           echo "Maven home ${M2_HOME}"
                           echo "Maven home ${PATH}"
                        sh "mvn spring-boot:build-image"
                    }
                }*/
    }
    
     
    
   
}

