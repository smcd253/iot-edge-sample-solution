stage('Checkout'){
  checkout scm
}

node {
  stage('Build') {
    azureIoTEdgePush dockerRegistryType: 'common', dockerRegistryEndpoint: [credentialsId: 'docker', url: 'michaeljqzq'], modulesToBuild: '*', azureCredentialId: 'azuresp', resourceGroup: 'zhiqing', rootPath: './'
  }
}