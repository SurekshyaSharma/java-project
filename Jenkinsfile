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
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '61682c97-ea62-4eac-8471-f69721cd2fad', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
        // some block
        sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins-p'
        }
}
}
