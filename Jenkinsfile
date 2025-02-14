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
                                                                          def absolutePath = WORKSPACE.replace('\\', '/').replace('C:', '/c')
                                                                          echo "Converted absolute path: ${absolutePath}"
                                                                          image 'ubuntu'
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
