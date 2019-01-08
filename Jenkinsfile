node {
    stage('Application_Build') {
        //git 'https://github.com/PritamDeb/spring-project.git'
        checkout scm
        bat 'mvn package -DskipTests'
    }
    stage('Application_Unit_Test') {
        //git 'https://github.com/PritamDeb/spring-project.git'
        bat 'mvn test'
        step([$class: 'Publisher'])
    }
    stage('Application_Code_Analysis') {
    //bat 'mvn sonar:sonar'
        withSonarQubeEnv {
        bat 'mvn sonar:sonar'
        }
    }
    stage('Application_Deploy_To_Test') {
        build 'Application_Deploy_To_Test'
    }
}