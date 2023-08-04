pipeline {
    agent {label 'jenkins-salve1 '}

    tools {
        maven "mymvn"
        jdk "myjava"
    }

    stages {
        stage('Compile') {
            steps {
                git 'https://github.com/bansode1990/DevOpsClassCodes.git'

                sh "mvn compile"

            }
        }
        stage('CodeReview') {
            steps {
                sh "mvn -P metrics pmd:pmd"

            }

        }
        stage('UnitTest') {
            steps {

                sh "mvn test"

            }

            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package') {
            steps {

                sh "mvn package"

            }

        }
    }
}
