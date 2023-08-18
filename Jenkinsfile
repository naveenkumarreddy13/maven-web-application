node{
    echo "jenkins branch is :${env.BRANCH_NAME}"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'RebuildSettings', autoRebuild: false, rebuildDisabled: false], [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * * ')])])
    
    def mavenHome = tool name: 'maven3.9.3'
    stage('checkout code'){
        git branch: 'development', credentialsId: '7ccfe0cc-1655-48f3-b717-aec7889f964c', url: 'https://github.com/naveenkumarreddy13/maven-web-application.git'
    }
    stage('Build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
    /*
    stage('Ececute sonarQube report'){
        sh "${mavenHome}/bin/mvn clean sonar:sonar"
    }
    stage('upload Artifacts into nexus'){
        sh "${mavenHome}/bin/mvn clean deploy"
    }
    stage('Deploy Application into Tomcat server'){
        sshagent(['56d48765-9e88-4f3b-84ce-eac29b4cab0d']) {
        sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.2.238:/opt/apache-tomcat-9.0.76/webapps"
    }
    
}
*/
}
