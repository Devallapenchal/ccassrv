
properties([parameters([choice(choices: 'Dev\nQA\nUAT\nPROD', description: 'Select any environment for deploy', name: 'Environments'), text(defaultValue: 'CCAS,LGD,LTV,SBL', description: 'select component', name: 'Component'), text(defaultValue: '236645hhh5,236645hhh5,236645hhh5,236645hhh5', description: 'select commit ID', name: 'commit ID')]), pipelineTriggers([])])
def workspace
node
{
 stage('Checkout')
  {
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '74:39:e5:48:d4:b6:f6:c5:aa:58:c9:94:0a:42:a0:5e', url: 'git@github.com:Devallapenchal/ccassrv.git']]])
   workspace =pwd();
   
  }
  stage('Build')
  {
   env.PATH = "${tool 'Ant'}/bin:${env.PATH}"
   bat 'start cmd.exe /c'
   bat 'ant -f build.xml'
  }
 stage('Build Notification')
  {
   emailext mimetype: 'text/html', body: '${FILE,path="ccas.html"}', subject: 'notification', from: 'pdeva893@gmail.com', to: 'pdeva893@gmail.com'
  }
}
