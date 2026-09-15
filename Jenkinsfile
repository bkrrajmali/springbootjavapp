pipeline {
    agent any
    tool {
        maven 'maven'
    }

    stages {
        stage ('Checkout from Git') 
        {
            steps {
                git branch: 'prod' , url: 'https://github.com/bkrrajmali/springbootjavapp.git'
            }
        }
    }
}