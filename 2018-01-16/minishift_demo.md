# Service catalog on minishift quickstart

## Setting up openshift cluster
``` bash
export MINISHIFT_ENABLE_EXPERIMENTAL=y
minishift start --vm-driver kvm  --openshift-version 3.7.0 --service-catalog
oc login -u system:admin
```

## Verify Service Catalog
``` bash
oc projects | grep kube-service-catalog
```

## List Brokers, Classes
``` bash
kubectl  get clusterservicebrokers -o yaml
oc get clusterserviceclasses --all-namespaces \
  -o custom-columns=NAME:.metadata.name,DISPLAYNAME:spec.externalMetadata.displayName
```

## Create Ansible Service Broker
``` bash
oc new-project ansible-service-broker
curl -s https://raw.githubusercontent.com/openshift/ansible-service-broker/master/templates/simple-broker-template.yaml | \
  oc process -n "ansible-service-broker" -f - | oc create -f -
```

## List Service Classes from ASB
``` bash
oc get clusterserviceclasses --all-namespaces \
  -o custom-columns=NAME:.metadata.name,DISPLAYNAME:spec.externalMetadata.displayName | grep APB
```

## Cleanup
``` bash
minishift delete
```
