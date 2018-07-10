pipeline {
    agent any
    tools {
        maven 'Maven 3.5.4' //name of Maven Installer what you've choose
    }
    stages {
        stage ('Generate Project') {
            steps {
                sh "mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false"
            }
        }
        stage ('Package Project and get test result') {
            steps {
                sh "cd my-app && mvn package"
                junit '**/*.xml'   //generate raport of unit test 
            }
        }
        stage ('Run App') {
            steps {
                sh "cd my-app && java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App"
            }
        }
        stage ('Clear Workspace') {       //clear workspace for next builds 
            steps {                       //witout that next build will failed 
             cleanWs()                    //becouse mvn project will already exist
            }
        }
    }   
}
