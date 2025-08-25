# README
Repo for gcp marketplace Release listing

~~service account : digitalai-marketplace-service@digitalai-public.iam.gserviceaccount.com -- don't have keys for this~~

https://github.com/GoogleCloudPlatform/marketplace-k8s-app-tools/blob/master/docs/building-deployer-envsubst.md


1. Update version in manifest/application.yaml.template
2. Update version in schema.yaml
3. Commit changes
4. Open GCloud shell in GCP
5. Checkout this repo
6. Set env variables
    * `export REGISTRY=gcr.io/digitalai-public`
    * `export APP_NAME=release`. 
7. Run `docker build --tag $REGISTRY/$APP_NAME/deployer .`
8. Run `docker push $REGISTRY/$APP_NAME/deployer`
9. Additional Run `docker tag $REGISTRY/$APP_NAME/deployer $REGISTRY/$APP_NAME/deployer:<new-version>` & docker push $REGISTRY/$APP_NAME/deployer:<new-version>
    1. new-version should show increment in minor version not in patch like we do for patch
    2. From xl-release 24.1.2 to xl-release 24.1.21 we changed deployer from 24.1 to 24.2
10. Update version of `Digital AI K8` product in https://console.cloud.google.com/producer-portal/overview?project=digitalai-public page
    1. `Container image` -> Edit Proposed release
    2. Public git repo url : https://github.com/xebialabs/xl-release-kubernetes-helm-chart
    3. Deploy documentation URL : https://docs.digital.ai/release/docs/24.1/xl-platform/operator/xl-op-install-on-gke for 24.1
