properties([pipelineTriggers([githubPush()])])
node('linux') {
    
    stage ("Unit Test") {
        git url: 'https://github.com/SurekshyaSharma/java-project.git', branch: 'master'
        sh  "ant -f test.xml -v"
        
        junit "reports/result.xml"
    }
    
    stage("Build") {
        sh "ant -f build.xml -v"
       
    }
     stage("Deploy"){
        sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-*.jar s3://assignment-jenkins/'
    }
       
    stage ("Report"){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '0de52fec-f4c9-47bf-b217-6bc5587ccea9', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        // some block
        sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins-p'
        }
}
   
}
