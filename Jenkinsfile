// Sample Jenkins file template 
pipeline {
    agent { 
        node {
            label 'jenkins-agent'
            }
      }
 
  tools {nodejs "node"}
 
  stages {
    stage('Check NodeJS configuration') {
      steps {
        sh 'npm config ls'
      }
    }
    stage('Cloning Git') {
      steps {
        git(
                    url: "https://github.com/angelopaolosantos/nextjs-jenkins.git",
                    branch: "main",
                    changelog: true,
                    poll: true
                )
      }
    }
    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }
     
    stage('Run Lint') {
      steps {
         sh 'npm run lint'
      }
    }    
    stage('Run Jest') {
      steps {
         sh 'npm test'
      }
    }   
  }
}