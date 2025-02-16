pipeline {
    agent any
    stages {
        stage('one') {
            steps {
                echo 'Stage one running....'
            }
        }
        stage('two') {
            steps {
                input("Do you want to continue?")
            }
        }
        stage('three') {
            when {
                not {
                    branch "main"
                }
            }
            steps {
                echo "stage is running"
            }
        }
        stage('four') {
            parallel {
                stage('unit test') {
                    steps {
                        echo 'Unit test running....'
                    }
                }
                stage('Integration test') {
                    agent {
                        docker {
                            image 'ubuntu'
                        }
                    }
                    steps {
                        script {
                            def workspacePath = sh(script: 'pwd -W', returnStdout: true).trim()
                            echo "Converted workspace path: ${workspacePath}"
                            sh "echo 'Running inside Docker container'"
                        }
                    }
                }
            }
        }
    }
}


