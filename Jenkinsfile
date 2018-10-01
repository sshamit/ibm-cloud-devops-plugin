def publishPlugin() {
    stage('Publish Plugin') {
        withCredentials([usernamePassword(credentialsId: 'dlaprod_jenkinsIO_credentials', passwordVariable: 'JENKINS_PASS', usernameVariable: 'JENKINS_USER')]) {
            sh '''
                #!/bin/bash
                mvn clean
                mvn release:prepare release:perform -Dusername=${JENKINS_USER} -Dpassword=${JENKINS_PASS}
            '''

        }
    }
}

node(env.DEFAULT_JENKINS_AGENT) {

    try {
        checkout([$class: 'GitSCM', branches: [[name: '*/add_jeninsfile']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'dlaprod_github.com', url: 'https://github.com/jenkinsci/ibm-cloud-devops-plugin']]])
        publishPlugin()

    } catch (err) {
        throw err
    }
}
