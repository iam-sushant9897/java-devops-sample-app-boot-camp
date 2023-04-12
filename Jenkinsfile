pipeline {
    agent any
    stages {
         stage ('Installing maven') {
             steps {
                 sh 'sudo apt-get update -y && sudo apt-get upgrade -y'
                 sh 'sudo apt-get install -y wget tree unzip maven'
                }
            }
         stage ('Compiling and Running Test cases') {
             steps {
                 sh 'mvn clean'
                 sh 'mvn compile'
                 sh 'mvn test'
                }
            }
         stage ('Creating package') {
             steps {
                 sh 'mvn package'
                }
            }
    }
}
