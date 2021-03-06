# compute.azure.crossplane.io/v1alpha3 API Reference

Package v1alpha3 contains managed resources for Azure compute services such as AKS.

This API group contains the following Crossplane resources:

* [AKSCluster](#AKSCluster)
* [AKSClusterClass](#AKSClusterClass)

## AKSCluster

An AKSCluster is a managed resource that represents an Azure Kubernetes Engine cluster.


Name | Type | Description
-----|------|------------
`apiVersion` | string | `compute.azure.crossplane.io/v1alpha3`
`kind` | string | `AKSCluster`
`metadata` | [meta/v1.ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#objectmeta-v1-meta) | Kubernetes object metadata.
`spec` | [AKSClusterSpec](#AKSClusterSpec) | An AKSClusterSpec defines the desired state of a AKSCluster.
`status` | [AKSClusterStatus](#AKSClusterStatus) | An AKSClusterStatus represents the observed state of an AKSCluster.



## AKSClusterClass

An AKSClusterClass is a non-portable resource class. It defines the desired spec of resource claims that use it to dynamically provision a managed resource.


Name | Type | Description
-----|------|------------
`apiVersion` | string | `compute.azure.crossplane.io/v1alpha3`
`kind` | string | `AKSClusterClass`
`metadata` | [meta/v1.ObjectMeta](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.15/#objectmeta-v1-meta) | Kubernetes object metadata.
`specTemplate` | [AKSClusterClassSpecTemplate](#AKSClusterClassSpecTemplate) | SpecTemplate is a template for the spec of a dynamically provisioned AKSCluster.



## AKSClusterClassSpecTemplate

An AKSClusterClassSpecTemplate is a template for the spec of a dynamically provisioned AKSCluster.

Appears in:

* [AKSClusterClass](#AKSClusterClass)




AKSClusterClassSpecTemplate supports all fields of:

* [v1alpha1.ClassSpecTemplate](../crossplane-runtime/core-crossplane-io-v1alpha1.md#classspectemplate)
* [AKSClusterParameters](#AKSClusterParameters)


## AKSClusterParameters

AKSClusterParameters define the desired state of an Azure Kubernetes Engine cluster.

Appears in:

* [AKSClusterClassSpecTemplate](#AKSClusterClassSpecTemplate)
* [AKSClusterSpec](#AKSClusterSpec)


Name | Type | Description
-----|------|------------
`resourceGroupName` | string | ResourceGroupName is the name of the resource group that the cluster will be created in
`resourceGroupNameRef` | [ResourceGroupNameReferencerForAKSCluster](#ResourceGroupNameReferencerForAKSCluster) | ResourceGroupNameRef - A reference to a ResourceGroup object to retrieve its name
`location` | string | Location is the Azure location that the cluster will be created in
`version` | string | Version is the Kubernetes version that will be deployed to the cluster
`vnetSubnetID` | Optional string | VnetSubnetID is the subnet to which the cluster will be deployed.
`vnetSubnetIDRef` | [SubnetIDReferencerForAKSCluster](#SubnetIDReferencerForAKSCluster) | ResourceGroupNameRef - A reference to a VnetSubnet object to retrieve its ID
`nodeCount` | Optional int | NodeCount is the number of nodes that the cluster will initially be created with.  This can be scaled over time and defaults to 1.
`nodeVMSize` | Optional string | NodeVMSize is the name of the worker node VM size, e.g., Standard_B2s, Standard_F2s_v2, etc.
`dnsNamePrefix` | Optional string | DNSNamePrefix is the DNS name prefix to use with the hosted Kubernetes API server FQDN. You will use this to connect to the Kubernetes API when managing containers after creating the cluster.
`disableRBAC` | Optional bool | DisableRBAC determines whether RBAC will be disabled or enabled in the cluster.
`writeServicePrincipalTo` | [v1alpha1.SecretReference](../crossplane-runtime/core-crossplane-io-v1alpha1.md#secretreference) | WriteServicePrincipalSecretTo the specified Secret. The service principal is automatically generated and used by the AKS cluster to interact with other Azure resources.



## AKSClusterSpec

An AKSClusterSpec defines the desired state of a AKSCluster.

Appears in:

* [AKSCluster](#AKSCluster)




AKSClusterSpec supports all fields of:

* [v1alpha1.ResourceSpec](../crossplane-runtime/core-crossplane-io-v1alpha1.md#resourcespec)
* [AKSClusterParameters](#AKSClusterParameters)


## AKSClusterStatus

An AKSClusterStatus represents the observed state of an AKSCluster.

Appears in:

* [AKSCluster](#AKSCluster)


Name | Type | Description
-----|------|------------
`clusterName` | string | ClusterName is the name of the cluster as registered with the cloud provider.
`state` | string | State is the current state of the cluster.
`providerID` | string | ProviderID is the external ID to identify this resource in the cloud provider.
`endpoint` | string | Endpoint is the endpoint where the cluster can be reached
`appObjectID` | string | ApplicationObjectID is the object ID of the AD application the cluster uses for Azure APIs.
`servicePrincipalID` | string | ServicePrincipalID is the ID of the service principal the AD application uses.
`runningOperation` | string | RunningOperation stores any current long running operation for this instance across reconciliation attempts.


AKSClusterStatus supports all fields of:

* [v1alpha1.ResourceStatus](../crossplane-runtime/core-crossplane-io-v1alpha1.md#resourcestatus)


## ResourceGroupNameReferencerForAKSCluster

ResourceGroupNameReferencerForAKSCluster is an attribute referencer that resolves name from a referenced ResourceGroup

Appears in:

* [AKSClusterParameters](#AKSClusterParameters)




ResourceGroupNameReferencerForAKSCluster supports all fields of:

* github.com/crossplane/stack-azure/apis/v1alpha3.ResourceGroupNameReferencer


## SubnetIDReferencerForAKSCluster

SubnetIDReferencerForAKSCluster is an attribute referencer that resolves name from a referenced ResourceGroup

Appears in:

* [AKSClusterParameters](#AKSClusterParameters)




SubnetIDReferencerForAKSCluster supports all fields of:

* github.com/crossplane/stack-azure/apis/network/v1alpha3.SubnetIDReferencer


This API documentation was generated by `crossdocs`.