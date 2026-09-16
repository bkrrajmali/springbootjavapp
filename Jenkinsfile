pipeline {
    agent any
    tools {
        maven 'maven'
    }
    environment {
        ACR_SERVER = 'democontainerregi.azurecr.io'
        IMAGE_NAME = 'springbootjavaapp'
        IMAGE_TAG = 'latest'
    }
    stages {
        stage ('Checkout from Git') 
        {
            steps {
                git branch: 'prod' , url: 'https://github.com/bkrrajmali/springbootjavapp.git'
            }
        }
        stage ('Validate with Maven') 
        {
            steps {
                sh 'mvn validate'
            }
        }
        stage ('Compile with Maven')
        {
            steps {
                sh 'mvn compile'
            }
        }
        stage ('Test with Maven')
        {
            steps {
                sh 'mvn test'
            }
        }
        stage ('SonarQube Analysis')
        {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''
                    mvn sonar:sonar \
                        -Dsonar.organization=bkrrajmali \
                        -Dsonar.projectKey=sprinbootjavaapp \
                        -Dsonar.projectName=sprinbootjavaapp \
                        -Dsonar.java.binaries=target/classes
                        '''

                }
            }
        }
        stage ('Package with Maven')
        {
            steps {
                sh 'mvn package'
            }
        }
    }
    stage('Docker Build') {
        steps {
            sh '''
            docker build -t $ACR_SERVER/$IMAGE_NAME:$IMAGE_TAG .
        }
    }
}