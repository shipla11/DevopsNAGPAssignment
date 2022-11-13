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
       stage("Sonar Analysis"){
            steps{
            withSonarQubeEnv("TestSonarQubeScanner")
                {
		    sh "mvn org.sonarsource.scanner.maven:sonar-maven-plugin:2.5:sonar"        
                }
            }
        }
    post{
        success{
            bat "echo success"
            }
        }
   }
}
