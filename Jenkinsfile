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
    
   
}
