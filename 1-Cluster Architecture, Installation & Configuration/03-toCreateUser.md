new user is nothing but anyone with ca signed certificate which can authenticate to apiserver

user generate csr --> sign using ca cert --> signed crt can authenticate with api server

controler manger have component to manage csr, signing using ca
kind: CertificateSigningRequest
