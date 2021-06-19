# alias 
alias k=kubectl
alias kdelete="kubectl delete --grace-period=0 --force"
alias kdry="kubectl --dry-run=client -o yaml"


# install yq
apt-get install yq
yq eval deploy.yaml
