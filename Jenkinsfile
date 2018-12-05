properties([pipelineTriggers([githubPush()])])
node('linux') {
    
    stage ("GetInstances") {
        sh "aws ec2 describe-instances --region us-east-1"
    }
    stage("CreateInstance") {
        sh "aws ec2 run-instances --image-id ami-0080e4c5bc078760e --count 1 --instance-type t2.micro --key-name DEVops --security-group-ids sg-094b86f0f4772b2f2 --region us-east-1"
       
    }
       
}
