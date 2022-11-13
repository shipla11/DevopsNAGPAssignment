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
	   
	stage("Publish to Artifactory"){
            steps{
                rtMavenDeployer(
                    id: 'deployer',
                    serverId: 'JfrogServer',
                    releaseRepo: 'shipla.nagp',
                    snapshotRepo: 'shipla.nagp'
                )
                rtMavenRun(
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: 'deployer'
                    )
                rtPublishBuildInfo(
                    serverId:'JfrogServer',
                )
            }        
        }
      }
    post{
        success{
            bat "echo success"
            }
        }
}
