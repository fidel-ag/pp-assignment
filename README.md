# Kubernetes Assignment 

Kubernetes Role-Based Access Control (RBAC) to manage permissions for two environments (Staging and Production) and two roles (Developer and Admin) along with secure access to AWS external RDS.

Assignment is on the basis that **kubectl** access has already been granted to the Kubernetes cluster. 


## Folder Description and Contents 

**1. environments:**

Root folder contains the **environments.yaml** file that creates namespaces for **staging** and **production**

A YAML file isn't really needed for this, you can as well run the following code:

``` bash
kubectl create ns staging
kubectl create ns production
```

**1.1 environments/staging**

production folder contains the **staging-roles.yaml** file that contains roles for developer and admin and access to the **staging** namespace

Staging folder also contains **developers-binding.yaml** file for a developers Group tied to the staging namespace, we've opted for a Group over User for the rolebinding for easier user management based on roles. 

**1.2 environments/production**

production folder contains the **production-roles.yaml** file that contains roles for admin to the *production* namespace

Production folder also contains **admin-binding.yaml** file for an admin Group tied to the production namespace, we've opted for a Group over User for the rolebinding for easier user management based on roles. 


**2.secrets**

Contains YAML files for secrets configuration for both the **staging** and **production** environments. 

Passwords for both YAML files have already been converted into base64. 


# Bonus Recommendations

1. Combine Kubernetes secrets with AWS IAM Roles for Service Accounts  
2. Use Network Policies to restrict communication to AWS RDS on a more specific level e.g on the basis of pod labels or IP address. 
3. Reduce the use of wildcards to grant full access on a role level, use the principle of least privilege to ensure roles are granted specific permissions for the tasks required to be executed. 
4. Always user Group scoped rolebindings over User rolebindings 
