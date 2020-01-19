node('qa') {

    stage 'Checkout'
        checkout scm
    stage 'Build & UnitTest'
    sh "sudo docker build -t accountownerapp:B${BUILD_NUMBER} -f Dockerfile ."
    sh "sudo docker build -t accountownerapp:test-B${BUILD_NUMBER} -f Dockerfile.Integration ."
    
    stage 'Pusblish UT Reports'
        
        containerID = sh (
            script: "sudo docker run -d accountownerapp:B${BUILD_NUMBER}", 
        returnStdout: true
        ).trim()
        echo "Container ID is ==> ${containerID}"
        sh "sudo docker cp ${containerID}:/TestResults/test_results.xml test_results.xml"
        sh "sudo docker stop ${containerID}"
        sh "sudo docker rm ${containerID}"
        step([$class: 'MSTestPublisher', failOnError: false, testResultsFile: 'test_results.xml'])    

}
