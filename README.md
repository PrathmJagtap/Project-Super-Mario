# Project-Super-Mario

## The First And Main Think Is The First Go To The AP-SOUTH-1 Region



#### Then Create 1 role and that role create 10 policies that mention below
![image](https://github.com/user-attachments/assets/313c7a91-2a82-438e-9b8f-dace89d6a7ae)

#### Then create 1 instance 
#### Configuration is instance type t2.medium, volume 30, SG All traffic allow
#### Then Attach role to this instance
#### Then login to the Instance 

#### Then setup
````
sudo apt update -y
````
#### Then setup docker
````
sudo apt install docker.io -y
sudo systemctl start docker
sudo usermod -aG docker ubuntu
newgrp docker
docker --version
````

#### Then install the terraform 

````
sudo apt-get update && sudo apt-get install -y gnupg software-properties-common

wget -O- https://apt.releases.hashicorp.com/gpg | \
gpg --dearmor | \
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null

gpg --no-default-keyring \
--keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
--fingerprint

echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update
sudo apt-get install terraform
terraform --version

````
#### Then install aws CLI 

````
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip 
unzip awscliv2.zip
sudo ./aws/install
aws --version
````
#### Then Install Kubectl

````
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
````

````
 curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
````

````
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
````

````
chmod +x kubectl
mkdir -p ~/.local/bin
mv ./kubectl ~/.local/bin/kubectl
````

````
kubectl version --client
````

#### Building Infrastructure Using terraform
````
sudo apt install git -y
git clone https://github.com/PrathmJagtap/Project-Super-Mario.git
````
#### Then Config The AWS

````
aws configure --profile eks
````
##### Give Access key And Secret Key

````
cd Project-Super-Mario
````
#### Then Go To The EKS-TF
````
cd EKS-TF
````
#### Then Edit Provide File
````
sudo vim provider.tf
````
![image](https://github.com/user-attachments/assets/ec296550-6255-41ad-bd84-a357ce6cfba0)

#### Then Create 1 bucket And That Bucket name copy and paste backend.tf file

````
sudo vim backend.tf
````
![image](https://github.com/user-attachments/assets/cad9dfc3-36ca-4e05-92c3-3af674b1f378)

#### Then Below Command
````
terraform init
terraform plan
terraform apply --auto-approve
````
````
aws eks update-kubeconfig --name EKS_CLOUD --region ap-south-1 --profile eks
````
````
cd ..
````
````
kubectl apply -f deployment.yaml
````
````
kubectl apply -f service.yaml
kubectl get all
kubectl get svc mario-service
````
#### copy the load balancer ingress and paste it on browser and your game is running

![Screenshot 2024-12-03 222835](https://github.com/user-attachments/assets/81667746-e1f2-4b3a-a259-6a6eafa8fbfc)


#### The Output is
![Screenshot 2024-12-03 222817](https://github.com/user-attachments/assets/6b4234c6-b7cc-4ec2-aa30-7aa9274e98ec)
