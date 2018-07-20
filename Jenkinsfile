node {
  stage('Checkout'){
    checkout scm
  }

  stage('Build') {
    azureIoTEdgePush dockerRegistryType: 'common', dockerRegistryEndpoint: [credentialsId: 'docker', url: 'michaeljqzq'], modulesToBuild: '*', azureCredentialId: 'azuresp', resourceGroup: 'zhiqing', rootPath: './'
  }
}