#!groovy

pipeline {
    agent {
        // how the pipeline will be built
        docker {
            image 'adoptopenjdk/openjdk11:jdk-11.0.3_7'
            args '--network ci --mount type=volume,source=ci-maven-home,target=/root/.m2'
        }
    }

    environment {
        // properties or environment variables, new or derived
        ORG_NAME = "deors"
        APP_NAME = "workshop-pipelines"
        APP_CONTEXT_ROOT = "/"
        APP_LISTENING_PORT = "8080"
        TEST_CONTAINER_NAME = "ci-${APP_NAME}-${BUILD_NUMBER}"
        DOCKER_HUB = credentials("${ORG_NAME}-docker-hub")
    }

    stages {
        stage('stage-1-name') {
            steps {
                // steps for stage 1 come here
                echo "stage-1"
            }
        }


        stage('stage-n-name') {
            steps {
                // steps for stage n come here
                echo "stage-2"

            }
        }
    }

    post {
        // post-process activities, e.g. cleanup or publish
        always {
            echo "-=- remove deployment -=-"
            // sh "docker stop ${TEST_CONTAINER_NAME}"
        }
    }
}
