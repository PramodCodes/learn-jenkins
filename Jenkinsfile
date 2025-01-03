// Jenkinsfile (Declarative Pipeline) 
pipelne{
    agent {
        // run on the AGENT-1 node
        node {
            label 'AGENT-1'
        }
    }
    // parameters section, this section is used to define the parameters that can be used in the pipeline
   parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    environment {
        // define the environment variables canbe accesed globally ,the following are additional to existing environment variables
        Greeting = 'Hello'
    }
    options {
        // timeout for the pipeline, if the pipeline is running more than 1 hour it will be aborted
        timeout(time: 1, unit: 'HOURS')
    }
    options {
        disableConcurrentBuilds()
    }
    //build stages
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                sh"""
                    echo 'env var printing in shell script'
                    env
                """
                
            }
        }
        stage('print params') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }
    }
    // post section
    post {
        always {
            echo 'This will always run irrespective of status of the pipeline'
        }
        failure {
            echo 'This will run only if the pipeline is failed, We use thsi for alerting the team' 
        }
        success {
            echo 'This will run only if the pipeline is successful'
        }
    }
}
