pipeline {
   agent any
   stages {
      stage('SCM') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/sri008/Trading-UI.git'
         }
      }
      stage('Build') {
         steps {
            sh '''
            npm install
            npm run build
            npm audit fix
            '''
          }
       }
      stage('Deploy') {
         steps {
            sh '''
            cp -r $WORKSPACE/build /opt/apache-tomcat-9.0.36/webapps
            curl -u admin:admin http://35.170.73.70:8888/manager/reload?path=/build
            '''
         }
      }
   }
}
