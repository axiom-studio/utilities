## Script to generate cluster-admin tokens

Use the below command directly on a bastion/local machine where you have the kubeconfig present
### Quick Generate (Recommended)

If you're generating tokens to attach it to a Axiom Studio cluster, create a `axiomcd` namespace in the cluster using the following command:
```bash
kubectl create namespace axiomcd
```
Run the following command to generate the cluster-admin tokens/kubeconfig
```bash
curl -O https://raw.githubusercontent.com/axiom-studio/utilities/main/kubeconfig-exporter/kubernetes_export_sa.sh && bash kubernetes_export_sa.sh cd-user axiomcd
```

### Custom Generate
If you want to make some changes to the default configurations, please follow the steps below to generate cluster-admin tokens:
1. If you're generating tokens to attach it to a Axiom cluster, create a `axiomcd` namespace in the cluster using the following command:
```bash
kubectl create namespace axiomcd
```
2. Clone the repository https://github.com/axiom-studio/utilities.git
```bash
git clone https://github.com/axiom-studio/utilities.git
```
3. Make sure you're inside `kubeconfig-exporter` folder and run the below command
```bash
bash kubernetes_export_sa.sh cd-user axiomcd 
```
4. If you want to automatically add the cluster to axiom studio, run the following command
```bash
bash kubernetes_export_sa.sh cd-user axiomcd [--axiom-endpoint=<value>] [--axiom-api-token=<value>][--cluster-name=<value>] [--insecure=<value>] [--server_url=<value>]
```
Parameter Descriptions:
- axiom-endpoint: The endpoint where axiom is running. For example - https://axiom.example.com
- axiom-api-token: API token for authentication with Axiom Studio. You can generate it from Global configurations > Authorization > API Tokens
- cluster-name: The name of the Kubernetes cluster to be added to Axiom Studio.
- server_url: The API server URL of the Kubernetes cluster. Recommended to map the url with a DNS endpoint.
- insecure (optional, default: true): Set to false to specify TLS creds for the api server url.
