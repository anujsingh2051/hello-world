pipeline {

    agent any



    environment {

        MAVEN_HOME = '/usr/share/maven' // Path to Maven installation

       

    }



    stages {

        stage('Checkout Code') { // Clones the repository

            steps {

                git 'https://github.com/anujsingh2051/hello-world.git'

            }

        }



        stage('Build with Maven') { // Builds the project and creates JAR/WAR

            steps {

                sh 'mvn clean package'

            }

        }



        stage('Run Unit Tests') { // Executes unit tests

            steps {

                sh 'mvn test'

            }

        }
        

    }


    pipeline {
    agent any 
    
    stages { 
        stage('SCM Checkout') {
            steps{
           git branch: 'master', url: 'https://github.com/anujsingh2051/hello-world'
            }
        }
        // run sonarqube test
        stage('Run Sonarqube') {
            environment {
                scannerHome = tool 'lil-sonar-tool';
            }
            steps {
              withSonarQubeEnv(credentialsId: 'gen-token', installationName: 'lil sonar installation') {
                sh "${scannerHome}/bin/sonar-scanner"
              }
            }
        }
    }
}



    post {

        success {

            echo 'Build and deployment successful!'

        }

        failure {

            echo 'Build failed!'

        }

    }

}
