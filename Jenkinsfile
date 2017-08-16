#!groovy

def checkout() {
    stage ('Checkout') {
        checkout([
            $class: 'GitSCM',
            branches: scm.branches,
            doGenerateSubmoduleConfigurations: scm.doGenerateSubmoduleConfigurations,
            extensions: scm.extensions + [[$class: 'CleanCheckout']],
            userRemoteConfigs: scm.userRemoteConfigs
        ])
    }
}

def dockerise() {
    stage ('Build Docker') {
        def project = "YOUR_PROJECT_NAME"

        img = docker.build("${project}/gcr-test", ".")

        docker.withRegistry("https://eu.gcr.io", "gcr:${project}") {
            img.push("${env.BUILD_TAG}")
            img.push("${env.BRANCH_NAME}")
        }
    }
}

node('SOME_JENKINS_NODE') {
    checkout()
    dockerise()
}
