def gv

pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage("init") {
            steps {
                script {
                   gv = load "script.groovy" 
                    echo "initialize application"
                }
            }
        }
        stage("build") {
            steps {
                script {
                    gv.buildApp()
                    echo "build application"
                }
            }
        }
        stage("test") {
            when {
                expression {
                    params.executeTests
                    echo "test application"
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    gv.deployApp()
                    echo "deploy application"
                }
            }
        }
    }   
}
