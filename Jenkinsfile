import groovy.json.JsonSlurper

def checkStatus() {
        def statusUrl = httpRequest authentication: 'jenkins_id', url: 'http://localhost:8080/job/WebLogicDeploy/lastBuild/api/json'
        def statusJson = new JsonSlurper().parseText(statusUrl.getContent())

        return statusJson['result']       

}

pipeline {
                agent {
                                label 'master'
                }
                tools{
                                maven 'MAVEN_HOME'
                }


 stages{

//node('master') {
 // stage('CheckOut') {
//    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'LocalGit', url: 'https://github.com/Abigail-A/Web_Application.git']]])
 // }
  stage('clean') {
    steps{
    bat label: '', script: 'mvn clean'
    }
  }
 stage('Build') {
   steps{
    bat label: '', script: 'mvn install'
   }
  }
  stage('deploy') {
   steps{
    build 'WebLogicDeploy'
   }
  }
stage('check Job status'){

        steps{
		script{
      /* if(checkStatus() == "RUNNING" ){
            timeout(time: 60, unit: 'MINUTES') {
            waitUntil {
                 def status = checkStatus()
		   status
                 return  (status == "SUCCESS" || status == "FAILURE" || status == "UNSTABLE" || status == "ABORTED")
          }
        }
        }*/


       if(checkStatus() == "RUNNING" ){
            timeout(time: 60, unit: 'MINUTES') {
       if( status != "SUCCESS" ){
            error('Stopping pipeline job because of other job failure')
        }
		else
		{
		echo 'successfully deployed'
		}
	    }
       }
		}
		}
}
 // stage('CopyArtifact') {
 //    bat label: '', script: 'xcopy C:\\Jenkins\\workspace\\BatchJob\\target\\WebApplication.war C:\\New_folder\\Jenkins_Artifact /y '
 //}
// stage('deploying artifact') {
//   bat 'cd C:\\New_folder\\Jenkins_Artifact\\WebApplication.war 
//      mvn weblogic:deploy'
 //  bat label: '', script: '''cd C:\\New_folder\\Jenkins_Artifact\\WebApplication.war
   //mvn weblogic:deploy'''
//}
}
}
