node {
    stage("scm") {
        git url: 'https://github.com/ismail2ov/picalculator'
    }
    stage("test and build") {
        sh "docker build -t ismail2ov/picalculator ."
    }
    stage("push") {
        withCredentials([[
            $class: 'UsernamePasswordMultiBinding', 
             credentialsId: 'docker_hub',
             usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD'
        ]]) {
            sh "docker login -u $USERNAME -p $PASSWORD"
            sh "docker push ismail2ov/picalculator"
        }
    }
}