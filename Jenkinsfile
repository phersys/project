node {

    properties([
            parameters([
                    string(name: 'dockerRegistry',
                            defaultValue: 'registry.hub.docker.com',
                            description: 'The docker registry to use (DNS name only)',),
                    string(name: 'dockerRepository',
                            defaultValue: 'apache/struts-showcase',
                            description: 'The repository to push to',),
                    string(name: 'dockerRegistryCredentialsId',
                            defaultValue: 'dockerhub-struts-credentials',
                            description: 'The Jenkins credentials id for docker registry to use',)
            ])
    ])

    stage('Checkout') {
        checkout scm
    }

    docker.image('maven').inside {
        withMaven() {
            stage('Maven Build') {
                sh '"$MVN_CMD" compile'
            }

            stage('Maven Build') {
                sh '"$MVN_CMD" test'
            }

            stage('Maven Build') {
                sh '"$MVN_CMD" package'
            }
            stage('Maven Build') {
                sh '"$MVN_CMD" clean install'
            }

        }

    }

    /*docker.withRegistry("https://${dockerRegistry}", "${dockerRegistryCredentialsId}") {

        stage('Docker Build') {
            image = docker.build("${dockerRegistry}/$(dockerRepository)", "--pull --no-cache .")
        }

        stage('Docker Push') {
            image.push()
        }
    }*/

}