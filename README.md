## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add <alias> https://<orgname>.github.io/helm-charts

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
<alias>` to see the charts.

To install the <chart-name> chart:

    helm install my-<chart-name> <alias>/<chart-name>

To uninstall the chart:

    helm delete my-<chart-name>


=====================================================================================

# Installation of Nginx controller through helm with https redirection with AWS ACM certificate

From now you can directly install the nginxcontroller with https redirection from the below helm charts,
 
with the latest version,  nginx 4.11.1
 
helm repo update
helm repo add nginx-ingress-ss https://sart-glitch.github.io/helm-charts/
helm install nginx-ingress nginx-ingress-ss/nginx-ingress-latest \
  --namespace nginx-ingress-new \
  --create-namespace \
  --set vpc.vpc_cidr="10.100.0.0/16" \
  --set nlb.acm="arn:aws:acm:us-east-1:851725167385:certificate/72da038a-ab0f-47f8-a9b8-a18210248ca8" \
  --set nlb.public_subnets="subnet-09fc3b10cf1783e41\,subnet-05e763f7e13075284" \
  --set nlb.nlb_name="Illusto-LB"

