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
        
       // Deploy is written in another jenkins job 
        
    }
