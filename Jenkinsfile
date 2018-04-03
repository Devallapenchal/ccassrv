def workspace;
node
{
 Stages
 {
  Stage('Checkout')
  {
   checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '62154932-8f6d-49d4-950e-9dcf30b2b0bb', url: 'git@github.com:Devallapenchal/ccassrv.git']]])
   workspace =pwd()
  }
  Stage('Build')
  {
   env.PATH = "${tool 'Ant'}/bin:${env.PATH}"
   bat 'ant -f build.xml'
  }
 }
}
