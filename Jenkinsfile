pipeline{
  agent any
  stages{
          stage('one'){
                       steps{
                             echo 'Stage one running....'
                            }
                      }
          stage('two'){
                          steps{
                                input("Do you want to continue?") 
                               } 
                      }
           stage('three'){
                          when{
                               not{
                                    branch "main"
                                  }
                              }
                          steps{
                                 echo "stage is running" 
                               }
                         }
           stage('four'){
                         parallel{
                                 stage('unit test'){
                                                    steps{
                                                          echo 'Unit test running....' 
                                                         }
                                                   }
                                 stage('Integration test'){
                                                           agent{
                                                                  docker{
                                                                          image 'ubuntu'
                                                                        }
                                                                  stages {
                                                                   stage('Build') {
                                                                          steps {
                                                                          script {
                                                                  docker.image('ubuntu').inside {
                                                                          sh 'echo "Running inside Docker container"'
                    }
                }
            }
        }
    }
                                                                }
                                                           steps{
                                                                 echo 'Running integration test....'
                                                                }
                                                          }
                                }
                        }
        }
        }  
