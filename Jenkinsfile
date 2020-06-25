node('master') {
  stage('CheckOut') {
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'LocalGit', url: 'https://github.com/Abigail-A/Web_Application.git']]])
  }
  stage('Build') {
    bat label: '', script: 'mvn clean install'
  }
 // stage('CopyArtifact') {
 //    bat label: '', script: 'xcopy C:\\Jenkins\\workspace\\BatchJob\\target\\WebApplication.war C:\\New_folder\\Jenkins_Artifact /y '
 //}
 stage('deploying artifact') {
    bat 'mvn -f C:\\Jenkins\\workspace\\BatchJob\\target\\WebApplication.war weblogic:deploy'
}
}
