pipeline {
    agent any

     stages {
        stage('CLONE') {
            steps {
                git branch: 'master', url: 'https://github.com/08dilipkumar/simple-java-maven-app.git'
            } 
        }
        stage('CLEAN') {
            steps {
                sh 'mvn clean'
            }
        } 

        stage('TEST') {
            steps {
                sh 'mvn test'
            }
        }   
         stage('REPORT') {
            steps {
                sh 'mvn sonar:sonar'
            }
        }   
        stage('BUILD') {
            steps {
                sh 'mvn package'
            }
        }  
        stage('archiveArtifacts') {
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }  
        stage('JACOCO-REPORT') {
            steps{
                jacoco buildOverBuild: true, changeBuildStatus: true, deltaBranchCoverage: '80', deltaClassCoverage: '80', deltaComplexityCoverage: '80', deltaInstructionCoverage: '80', deltaLineCoverage: '80', deltaMethodCoverage: '80', maximumBranchCoverage: '80', maximumClassCoverage: '80', maximumComplexityCoverage: '80', maximumInstructionCoverage: '80', maximumLineCoverage: '80', maximumMethodCoverage: '80', minimumBranchCoverage: '80', minimumClassCoverage: '80', minimumComplexityCoverage: '80', minimumInstructionCoverage: '80', minimumLineCoverage: '80', minimumMethodCoverage: '80'
            }
        }
    }
}
