# Azure_Deployment_of_Container_on_AKS
This Azure Pipelines Task allows users to easily deploy their application source to an Azure Kubernetes Service (AKS) cluster in their Azure Pipelines workflow. 

## Pipeline Requirements

This task requires the following parameters to be defined:

Parameters:

| Name  | type | Default | Values | Opional/Required | Comments |
| ------------- | :-------------: | :-------------: | :-------------: | :-------------: | ------------- |
| deploymentType | string | | | Required | |
| dockerImageTag | string | | | Required | |
| azureSubscription | string | | | Required | |
| resourceGroup | string | | | Required | |
| kubernetesName | string | | | Required | |
| helmRelease | string | | | Required | |
| helmChart | string | | | Required | |
| maxReleaseHistorys | string | | | Required | |
| namespace | string | | | Required | |
| helmValuesFile | string | | | Required | |
| imageRepository | string | | | Required | |


These parameters provide multiple use case options for the template, enable/disable flags for the utilization of different templates as per the requirements.


## Use Cases

You can directly call a particular template as per the requirement. for example: 

  ```yaml
  # azure-pipeline.yml
  resources:
  repositories:
    - repository: Template
      type: github
      name: your_username/Azure_Deployment_of_Container_on_AKS
      ref: <respective branch name>
      endpoint: 'githubServiceConnectioNname'

  steps:
  # passing the parameters
  - template: ContainerDeploymentByHelmOnAKS.yaml
    parameters:
      deploymentType: ${{ parameters.deploymentType}}
      dockerImageTag: ${{ parameters.dockerImageTag }}
      azureSubscription: ${{ parameters.azureSubscription }}
      resourceGroup: ${{ parameters.resourceGroup }}  
      kubernetesName: ${{ parameters.kubernetesName }}
      helmRelease: ${{ parameters.helmRelease }}             
      helmChart: ${{ parameters.helmChart }}            
      maxReleaseHistorys: ${{ parameters.maxReleaseHistorys }}                 
      namespace: ${{ parameters.namespace }}
      helmValuesFile: ${{ parameters.helmValuesFile }}
      imageRepository: ${{ parameters.imageRepository }}
        
  
Make sure to adjust the repository name, branch name, and parameter values according to your project's requirements.

  ```
