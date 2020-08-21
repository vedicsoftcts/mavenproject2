pipeline {
    agent any

    tools {
        maven "M3"
    }

    stages {
        stage("resources"){
            steps{
                // Get some code from a GitHub repository
                git 'https://github.com/vedicsoftcts/mavenproject2.git'
            }
        }
        stage("clean"){
            steps {
                // Run Maven on a Windows agent.
                bat "mvn -Dmaven.test.failure.ignore=true clean "       
            }
        }
        stage("compile"){
            steps {
                 // Run Maven on a Windows agent.
                bat "mvn clean compile "
             }
        }
        stage("test"){
            steps {
                echo "maven project testing....."
                bat "mvn clean test "
            }
        }
    }
    post {
                // If Maven was able to run the tests, even if some of the test
                // failed, record the test results and archive the jar file.
        success {
                echo "project maven all stage are successful..... "
                echo "now maven package..."
                bat "mvn clean package"
                //bat "mvn clean install"
        }
        failure{
                echo "project maven some stage may failed..... "
        }
    }
}
