# Consultas-AWS-Config


# Consulta S3
```bash
SELECT
  accountId,
  awsRegion,
  arn,
  configurationItemCaptureTime,
  configurationStateId,
  configuration,
  configurationItemStatus,
  resourceId,
  resourceName,
  tags,
  resourceType,
  resourceCreationTime,
  supplementaryConfiguration.ServerSideEncryptionConfiguration.rules,
  supplementaryConfiguration.ServerSideEncryptionConfiguration.rules.applyServerSideEncryptionByDefault.sseAlgorithm
WHERE
  resourceType = 'AWS::S3::Bucket'
  AND supplementaryConfiguration.ServerSideEncryptionConfiguration.rules.applyServerSideEncryptionByDefault.sseAlgorithm != 'aws:kms'
```

# Consulta grupos de seguridad y configuración de puertos
```bash
SELECT
  configurationItemCaptureTime,
  complianceType,
  complianceState,
  complianceContributorCount,
  configurationStateId,
  configurationStateMd5Hash,
  configurationItemVersion,
  configuration,
  configurationItemStatus,
  arn,
  accountId,
  resourceId,
  resourceName,
  awsRegion,
  tags,
  resourceType,
  resourceCreationTime,
  relatedEvents,
  relationships,
  configuration.ipPermissions.ipRanges.cidrIp,
  configuration.ipPermissions.ipProtocol,
  configuration.ipPermissions.fromPort,
  configuration.ipPermissions.toPort
WHERE
  resourceType = 'AWS::EC2::SecurityGroup'
```

# Instancias EC2
```bash
SELECT
  configurationItemCaptureTime,
  complianceType,
  complianceState,
  complianceContributorCount,
  configurationStateId,
  configurationStateMd5Hash,
  configurationItemVersion,
  configuration,
  configurationItemStatus,
  arn,
  accountId,
  resourceId,
  resourceName,
  awsRegion,
  tags,
  resourceType,
  resourceCreationTime,
  relatedEvents,
  relationships,
  configuration.instanceType,
  configuration.launchTime,
  configuration.imageId,
  configuration.vpcId,
  configuration.subnetId,
  configuration.privateIpAddress,
  configuration.publicIpAddress,
  configuration.securityGroups
WHERE
  resourceType = 'AWS::EC2::Instance'
```

