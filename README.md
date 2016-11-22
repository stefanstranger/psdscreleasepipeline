# psdscreleasepipeline
Design input on a PowerShell DSC Release Pipeline

I would like to recieve input on designing a Release Pipeline for PowerShell DSC deployments.

# Scenario
Implement a Release Pipeline for the deployment of PowerShell Desired State Configurations.

The goal is that all DSC Configurations and DSC Environment Configuration Data (separating Configuration and Environment Data)
will be stored in Source Control and the Release Pipeline will continue to help deploy the Desired State Configuration to the Target Nodes.

The following highlevel DSC Deployment steps need to be implemented within the Release Pipeline:

1. Create DSC Configuration script
2. Commit DSC Configuration script
3. Create Environmental DSC Configuration script
4. Compile MOF file
5. Rename MOF file to [Guid].mof file
5. Create Checksum file for [Guid].mof file
6. Copy [Guid].mof and Checksum files to Pull Server


# Environment
- Domain Environment
- Domain Controllers
- A minimum of two or more DSC Pull Servers behind a Load Balancer
- Team Foundation Server 2015
- DSC Target Nodes with Windows Server 2016 OS
- Team Foundation Server 2015 will be used for:
     - Source Control 
     - Build
     - Test
     - Release
- Git Repository

# Release Pipeline Module
![Image](https://github.com/stefanstranger/psdscreleasepipeline/blob/master/Pictures/ReleasePipelineModel.png)
\* from Whitepaper The Release Pipeline Model.


# Design questions:
1. Which deployment tasks\steps should be in Build, Test and Release?
2. What should be tested?
3. How should be tested? (Pester?, PSScriptAnalyzer?)

You can find a first design overview [here](https://github.com/stefanstranger/psdscreleasepipeline/blob/master/Design/DSCConfigurationReleasePipeline.png) 

Can you please use the [repo issues](https://github.com/stefanstranger/psdscreleasepipeline/issues) for feedback.

A really appreciated all the feedback I can get.

/Stefan

# References
- [Whitepaper The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf)
- [Building a Release Pipeline with Team Foundation Server 2012](https://msdn.microsoft.com/en-us/library/dn449957.aspx)
- [Separating Configuration and Environment Data](https://msdn.microsoft.com/en-us/powershell/dsc/configData)