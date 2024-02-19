pipeline {
    agent any
    tools {
        maven 'MAVEN'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    // Build micropos-common
                    dir('micropos-common') {
                        sh 'mvn clean install'
                    }

                    // Build micropos-repository
                    dir('micropos-repository') {
                        sh 'mvn clean install'
                    }

                    // Build micropos-services
                    dir('micropos-services') {
                        sh 'mvn clean install'
                    }

                    // Build micropos-web
                    dir('micropos-web') {
                        sh 'mvn clean install'
                    }

                    // Build micropos-email
                    dir('micropos-email') {
                        sh 'mvn clean install'
                    }
                }
            }
        }
        
        stage('Deploy to Tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '4fd75e70-72d4-4eca-88f2-ceb50d550227', path: '', url: 'http://74.235.239.120/')], contextPath: '/java-webapp', war: '**/*.war'
            }
        }
    }
    
    // Add post-build actions if needed
}
