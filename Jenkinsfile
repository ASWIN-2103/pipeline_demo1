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
                                                                          args '-v $(pwd):/workspace -w /workspace'
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
