pipeline {
    agent any
    
    stages {
        stage ('Checkout from Git') 
        {
            steps {
                git branch: 'prod' , url: 'https://github.com/bkrrajmali/springbootjavapp.git'
            }
        }
    }
}