properties([pipelineTriggers([githubPush()])])
node('linux') {
    
    stage ("Unit Test") {
        sh "ant -f text.xml -v"
        junit "reports/result.xml"
    }
    stage("Build") {
        sh "ant -f build.xml -v"
       
    }
       
}
