## mig-operator

## Operator Installation
`oc create -f operator.yml`

## Velero Controller Installation

### For use only with [mig-operator](https://github.com/fusor/mig-operator)/[mig-controller](https://github.com/fusor/mig-controller)/[mig-ui](https://github.com/fusor/mig-controller)
1. Edit controller.yml
1. Adjust `restic_pv_host_path` for the version of Openshift you are using.
1. `oc create -f controller.yml`

### Standalone
To use velero standalone you must set up coordinates for a backup storage location. This does not prevent also using velero for migrations.

1. Edit controller.yml
1. Adjust `restic_pv_host_path` for the version of Openshift you are using.
1. Change `standalone` to `true`
1. Set up coordinates for an s3 bucket.
```
  aws_bucket_name:
  aws_key_id:
  aws_region:
  aws_secret_access_key:
```
1. If you want to use noobaa instead of AWS  use the same keys, and also set `noobaa` to `true`, and set `noobaa_service_url`.
1. `oc create -f controller.yml`

## Updating credentials
1. If you want to update credentials to your storage location using this operator you'll need to delete the `cloud-credentials` secret.

## TODO:
Figure out if we can look at capabilities to set restic_pv_host_path automatically.
