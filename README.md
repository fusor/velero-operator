## mig-operator

## Operator Installation
`oc create -f operator.yml`

## Migration Controller Installation
Edit controller.yml to set at a minimum:
```
  aws_bucket_name:
  aws_key_id:
  aws_region:
  aws_secret_access_key:
```

If you want to use noobaa you may use the same keys for credentials, set `noobaa` to `true`, and set `noobaa_service_url`.

`restic_pv_host_path` will need to be configured for Openshift 3 or 4.

`oc create -f controller.yml`

## TODO:
Figure out if we can look at capabilities to set restic_pv_host_path automatically.
