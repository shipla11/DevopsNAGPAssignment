pipeline{
    agent any
    	tools{
        maven 'Maven'
    }
    stages{
        stage("code checkout"){
            steps{
            bat "echo hello"
            }
        }   
        stage("code build"){
            steps{
            bat "mvn clean"
            }
        }
        stage("unit test"){
            steps{
            bat "mvn test"
            }
        }
        stage('Sonarqube Analysis'){
	    def scannerHome = tool 'TestSonarQubeScanner';
	    withSonarQubeEnv('SonarQubeScannerToken'){
	    sh "${scannerHome}/bin/sonar-scanner\
	    -D sonar.login=admin\
	    -D sonar.password=admin\
	    -D sonar.host.url=http://192.168.0.102:9000"     
                }
            }
        }
      
    }
    post{
        success{
            bat "echo success"
            }
        }
}
