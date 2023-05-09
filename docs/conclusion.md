# Conclusion

This has only been a brief overview of a few key concepts. You have been given a taste of the GitOps promise: consistent, declarative, rapid application deployments.

When the complexity of a orchestrating a deployment and traffic management is reduced by F5 XC Managed Kubernetes coupled with the power of NGINX Ingress Controller, developers can focus on their priority: the development of their applications.

## Lab Teardown

1. In the lab **devbox** VM, open a terminal and run the following script to initiate teardown of the infrastructure built for this lab:

    ```bash
    export TF_VAR_namespace=<your xc namespace here>
    cd ~/terraform-modular-demo-framework
    ./gitops-lab/teardown-lab-environment.sh 
    ```

    > **Note:** Ensure that the script has completed successfully before moving to the next step.

1. Next, run the following command to destroy the cloud credential resources used for this lab:

    ```bash
    terragrunt run-all destroy --terragrunt-modules-that-include ./env-setup.hcl --terragrunt-non-interactive
    ```

    > **Note:** Ensure that the script has completed successfully before disconnecting from the VM.

1. Shut down and delete the UDF deployment.

## END OF LAB
