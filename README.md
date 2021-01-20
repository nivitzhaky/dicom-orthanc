# orthanc

#AWS
chmod 400 ~/Downloads/awstest.pem
ssh -i ~/Downloads/awstest.pem ec2-user@ec2-34-234-204-3.compute-1.amazonaws.com

sudo yum update -y
sudo yum install -y docker
sudo service docker start
sudo yum install -y git
git clone https://github.com/nivitzhaky/dicom-orthanc.git
cd docker
sudo curl -L https://github.com/docker/compose/releases/download/1.20.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose -f docker-compose-aws.yml up -d