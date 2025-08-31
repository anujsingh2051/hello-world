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

         stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar') { // 'sonar' is the name of your SonarQube server in Jenkins
                    sh "${scannerHome}/bin/sonar-scanner"
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
