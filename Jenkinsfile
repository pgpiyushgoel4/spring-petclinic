pipeline{
    agent{label 'master'}
    tools{
        maven 'm3'
    }
    stages{
        stage('Checkout'){
            steps{
                git 'https://github.com/AnjuMeleth/spring-petclinic.git'
            }
        }
        stage('Build'){
            steps{
                 sh 'mvn clean compile'
            }
        }
        stage('Test'){
            steps{
                     sh 'mvn test'
                     junit '**/target/surefire-reports/TEST-*.xml'
            }
        }
        stage('Package'){
            steps{
                sh 'mvn package'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage('Deploy'){
            steps{
                sh echo "Tata@1234" | sudo -S pwd
		sh "sudo docker build . -t pgpiyushgoel4/petclinic"
		sh "sudo docker run -d -p 8091:8080 anjurose/petclinic"
                    
            }
        }
    }
}

