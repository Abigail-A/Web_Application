node('master') {
  stage('CheckOut') {
    checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'LocalGit', url: 'https://github.com/Abigail-A/Web_Application.git']]])
  }
  stage('Build') {
    bat label: '', script: 'mvn clean install'
  }
//stage('CopyArtifact') {
 //  bat label: '', script: 'xcopy C:\\Jenkins\\workspace\\PipelineEx\\target\\SpringIOC-1.0-SNAPSHOT.jar C:\\New_folder\\Jenkins_Artifact /y '
//}



}
