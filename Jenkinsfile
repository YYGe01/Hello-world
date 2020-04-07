#!/usr/bin/env groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'make' 
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true 
            }
        }
    }
stages {
        stage('Test') {
            steps {
                /* `make check` 在测试失败后返回非零的退出码；
                * 使用 `true` 允许流水线继续进行
                */
                sh 'make check || true' 
                junit '**/target/*.xml' 
            }
        }
    }


}
