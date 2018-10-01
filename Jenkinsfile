def publishPlugin() {
    stage('Publish Plugin') {
        withCredentials([string(credentialsId: 'dlaprod_jenkinsIO_credentials', passwordVariable: 'JENKINS_PASS', usernameVariable: 'JENKINS_USER')]) {
            sh '''
                #!/bin/bash
                mvn clean
                #mvn release:prepare release:perform -Dusername=${JENKINS_USER} -Dpassword=${JENKINS_PASS}
            '''

        }
    }
}

node(env.DEFAULT_JENKINS_AGENT) {

    try {
        publishPlugin()

    } catch (err) {
        throw err
    }
}
