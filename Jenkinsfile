node('master')
    {
        stage('clean'){
            ws('C:\\Jenkins_Code'){
            deleteDir()
            }
        }
        stage('checkout'){
            ws('C:\\Jenkins_Code') {
            
            checkout changelog: false, poll: false, scm: [$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/DhanrajDanny/webapp.git']]]
        
            }
        }
        stage('build'){
             ws('C:\\Jenkins_Code') {
                 bat '''
                 mvn clean package
                 echo build complted
                 '''
             }
        }
        stage('deploy'){
            bat '''
            copy C:\\Jenkins_Code\\target\\WebApp.war C:\\Tomcat\\webapps
            cd c:\\Tomcat\\bin
            net stop Tomcat9
            sleep 10
            net start Tomcat9
            '''
        }
        
    }