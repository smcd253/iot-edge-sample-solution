node {
  stage('Checkout'){
    checkout scm
  }

  stage('Build') {
    azureIoTEdgePush dockerRegistryType: 'common', dockerRegistryEndpoint: [credentialsId: 'docker', url: 'michaeljqzq'], modulesToBuild: '*', azureCredentialId: 'azuresp', resourceGroup: 'zhiqing', rootPath: './'
  }

  stage('Deploy') {
    azureIoTEdgeDeploy azureCredentialsId: 'azuresp', deploymentId: 'jenkins-deploy', deploymentType: 'single', deviceId: '123', iothubName: 'anotheriothub', priority: '0', resourceGroup: 'devkit-happypath-demo', rootPath: './', targetCondition: ''
  }
}