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
         stage ('Install sonarqube cli') {
             steps {
                sh 'wget -O sonar-scanner.zip https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.6.2.2472-linux.zip'
                sh 'unzip -o -q sonar-scanner.zip'
                sh 'sudo rm -r /opt/sonar-scanner'
                sh 'sudo mv --force sonar-scanner-4.6.2.2472-linux /opt/sonar-scanner'
                sh 'sudo sh -c \'echo "#/bin/bash \nexport PATH=\\\"$PATH:/opt/sonar-scanner/bin\\\"" > /etc/profile.d/sonar-scanner.sh\''
                sh 'ls /opt/sonar-scanner/bin'
                sh 'chmod +x /opt/sonar-scanner/bin/sonar-scanner'
                sh 'echo $PATH'
                sh 'cat /etc/profile.d/sonar-scanner.sh'
                sh '. /etc/profile.d/sonar-scanner.sh'
                sh '/opt/sonar-scanner/bin/sonar-scanner --version'
                sh 'ls'
                }
            }
    }
}
