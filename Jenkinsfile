pipeline {
    agent any
    tools {
        // Note: this should match with the tool name configured in your jenkins instance (JENKINS_URL/configureTools/)
        maven "maven"
    }
   stages {
        stage("clone code") {
            steps {
                script {
                    // Let's clone the source
                    git 'https://github.com/fareef/JenkinsWar.git';
                }
            }
        }
      stage("mvn build") {
            steps {
                script {
                    // If you are using Windows then you should use "bat" step
                    // Since unit testing is out of the scope we skip them
                    //bat(/${MAVEN_HOME}\bin\mvn -Dmaven.test.failure.ignore clean package/)
                     sh "mvn package"
      
        }
            }
        }
      stage('Deploy to Tomcat'){
         deploy adapters: [tomcat8(credentialsId: 'tomcat', path: '', url: 'http://15.207.84.25:8080/')], contextPath: null, war: '**/*.war'      
      }
