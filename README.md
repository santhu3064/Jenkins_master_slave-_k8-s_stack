Build all the docker image for master and slaves


Update the config.yaml in jenkins_kubestack folder with correct docker images.
update the secrete top create you github password as secret

echo -n "GITHUB PASSOERD" | base64  

update the output to GITHUB_PASSWORD in secerts.yaml

Run kubectl create -f jenkins_kube_stack/
