
properties([parameters([choice(choices: 'Dev\nQA\nUAT\nPROD', description: 'Select any environment for deploy', name: 'Environments'), text(defaultValue: 'CCAS,LGD,LTV,SBL', description: 'select component', name: 'Component'), text(defaultValue: '236645hhh5,236645hhh5,236645hhh5,236645hhh5', description: 'select commit ID', name: 'commit ID')]), pipelineTriggers([])])
def workspace
node
{
 stage('Checkout')
  {
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62154932-8f6d-49d4-950e-9dcf30b2b0bb', url: 'git@github.com:Devallapenchal/ccassrv.git']]])
   workspace =pwd();
   
  }
  stage('Build')
  {
   env.PATH = "${tool 'Ant'}/bin:${env.PATH}"
   bat 'ant -f build.xml'
  }
 stage('Build Notification')
  {
   emailext ( subject: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'", attachmentsPattern: "'file:///F:/programs/programs/ccas.html'", body: """

STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':

Check console output at "${env.JOB_NAME} [${env.BUILD_NUMBER}]"

""", from: 'pdeva893@gmail.com', to: 'pdeva893@gmail.com')
  }
}
