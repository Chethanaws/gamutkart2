pipeline{
     agent any

           stages{
      
               stage('clone repo') {
                           steps{
                            checkout scm
                }
            }
               stage('build'){
                          steps{
                            'sh mvn install -Dmaven.test.skip=true' 
                       }
               }
              
               stage('junit') {
                         steps{
                            sh 'mvn complier:testCompile'
                            sh 'mvn surefire:test'
                            junit 'target/**/*.xml'
                             }
                     }
               stage('Deployment') {
                      steps{
                           sh 'sshpass -p "Ag" scp tagert/gamutgurus.war AG@172.17.0.3:/home/AG/apache-tomcat-9.0.70/webapps'
                           sh 'sshpass -p "Ag" ssh AG@172.17.0.3 "/home/AG/apache-tomcat-9.0.70/bin/startup.sh" '
                  } 
           }

     }
}
   
