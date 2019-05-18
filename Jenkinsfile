pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }


       // stage ('Deployment Stage') {
         //   steps {
           //     withMaven(maven : 'LocalMaven') {
             //       sh 'mvn deploy'
               // }
            //}
       // }
        
        stage ( 'sonarstage' ) {
            steps { 
                withSonarQubEnv( 'sonar') {
                    withMaven(maven : 'LocalMaven' ) {
                    sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
        stage ('sonar install') {
            steps {
                withSonarQubeEnv('sonar') {
                    withMaven(maven : 'LocalMaven') {
                        sh 'mvn clean install sonar:sonar'
                    }
                }
            }
        }
                        
        
    }
}
