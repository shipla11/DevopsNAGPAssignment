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
		    sh "mvn clean package sonar:sonar"    
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
