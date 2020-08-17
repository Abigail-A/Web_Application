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
