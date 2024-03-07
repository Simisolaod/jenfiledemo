pipeline{
    tools{
        maven 'mymaven'
    }
    
    agent any
    
    parameters{
        choice(name: 'Env',choices:[' ', 'Dev', 'QA'])
    }
    
    stages{
        stage('clone')
        {
            steps{
                git'https://github.com/Sonal0409/DevOpsCodeDemo.git'
            }
        }
        stage ('Build in Env')
        {
            when {expression{params.Env == 'Dev'}}
            steps{
                sh 'mvn pmd:pmd'
                sh 'mvn package'
            }
        }
        stage ('Build in test')
        {
            when{expression{params.Env == 'QA'}}
            steps{
                sh 'mvn test'
                sh 'mvn package'
            }
        }
        
    }
}
