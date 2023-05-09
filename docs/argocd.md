# ArgoCD

[ArgoCD](https://argoproj.github.io/cd/) is a declarative, GitOps continuous delivery tool for Kubernetes.

ArgoCD is the tool we will be using to watch your lab repository for changes, and automatically deploy updated resources to Kubernetes for you. ArgoCD runs as a Kubernetes application itself, and "pulls" in applications to the cluster it runs on, or other external clusters. ArgoCD has already been installed for you in your lab cluster.

In addition to deploying applications for the first time, ArgoCD can be used to ensure the state of your application remains consistent with an application's configuration stored in Git. ArgoCD continuously monitors the state of application configuration in Git, and compares it to the state of the deployed application in Kubernetes. ArgoCD will update an application's state if it detects configuration drift.

This is a fundamental tenet of GitOps: Source control is the source of truth for an application (or infrastructure), and configuration changes to a deployed application outside of this process will not be tolerated, and will be corrected by ArgoCD.

## Login to ArgoCD

1. Run this command in your Visual Studio Code terminal to find your assigned namespace for this lab:

    ```bash
    export XC_NAMESPACE=`cat ~/terraform-modular-demo-framework/tf_output_vars.yaml | yq '.namespace'`
    echo $XC_NAMESPACE
    ```

1. In your browser, open a new tab and navigate to `https://argocd-<your namespace>.labs.f5demos.com`

> ***Note:*** It may take some time for ArgoCD to fully deploy and initialize before it is available via web browser.

1. Obtain the ArgoCD password by running the following from a terminal in the **devbox** vm:

    ```bash
    cat ~/terraform-modular-demo-framework/tf_output_vars.yaml | yq '.argocd_password'
    ```

1. Login with the `admin` user and the password you obtained above.

1. In the ArgoCD UI, note that there are no applications:

    <img src="assets/argocd-empty.png" alt="ArgoCD with no projects" width="700"/>

Next, we will deploy additional applications to your Kubernetes cluster leveraging ArgoCD.

[Continue to next section...](infra-apps.md)
