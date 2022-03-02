# custom-actions
This repo is for public composite actions to use by other workflows

A deploy example from workflow:
```yaml
deploy:
  runs-on: ubuntu-latest

  steps:
    - name: 'Checkout repo'
      uses: actions/checkout@main

    - name: 'Deploy to AKS'
      uses: Gemeente-DenHaag/custom-actions/deploy-to-aks@v0.0.1
      with:
        credentials: '${{ secrets.SUPERSECRET_CREDENTIALS }}'
        resource-group: '${{ secrets.SUPERSECRET_RG }}'
        cluster-name: '${{ secrets.SUPERSECRET_CL_NAME }}'
        repo: my-chart-repo # optional, default https://gemeente-denhaag.github.io/helm-charts
        chart: generic # optional, default generic
        release-name: my-release
        values-file: values.yaml
        namespace: my-namespace
        full-image-url: test.azurecr.io/myacr:latest
        extra-params: '--set name=my-name --set other.override=thisone' # optional