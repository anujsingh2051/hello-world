pipeline {

    agent any



    



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
        stage('Code Analysis with SonarQube') {
            environment {
                SONARQUBE_SERVER = 'sonarqube' // Replace with your SonarQube installation name configured in Jenkins
            }
            steps {
                withSonarQubeEnv(SONARQUBE_SERVER) {
                    sh 'mvn sonar:sonar'
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
