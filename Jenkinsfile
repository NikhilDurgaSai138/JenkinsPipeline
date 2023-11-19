pipeline {
    agent any 
        stages {
            stage('One') {
                steps {
                    echo "This is the first stage"
                }
            }
            stage('two') {
                steps {
                    input('Do you want to proceed')
                }
            }
            stage('three') {
                when {
                    not {
                        branch 'master'
                    }
                }
                steps {
                    echo 'Hello'
                }
            }
            stage('four') {
                parallel {
                    stage('unit test') {
                        echo 'running unit test'

                    }
                    stage('integration test') {
                        agent {
                            docker {
                                reuseNode false
                                image 'ubuntu'
                            }
                            steps {
                                echo 'running integration test'
                            }
                        }


                    }
                }
            }
        }
    
}
