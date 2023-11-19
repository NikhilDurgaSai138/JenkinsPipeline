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
                    stage('Unit Test') {
                        steps {
                            echo 'running unit test'


                        }
                        
                    }
                    stage('Integration test') {
                        agent none {
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
