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


https://book.orthanc-server.com/users/rest.html

dicom commands:
curl -X PUT http://localhost:8042/tools/log-level -d "verbose"



docker run --name some-postgres -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=pgpassword --rm postgres
docker run -it --link some-postgres:postgres --rm postgres sh -c 'echo "CREATE DATABASE orthanc;" | exec psql -h "$POSTGRES_PORT_5432_TCP_ADDR" -p "$POSTGRES_PORT_5432_TCP_PORT" -U postgres'

"PostgreSQL" : {
"EnableIndex" : true,
"EnableStorage" : true,
"Host" : "172.17.0.38",
"Port" : 5432,
"Database" : "orthanc",
"Username" : "postgres",
"Password" : "pgpassword"
}

storescu localhost 4242 ./images/IMG0001.dcm  +sd -ll info  -aec ORTHANC
findscu -W 127.0.0.1 4242 -k 0008,0050="*"
dump2dcm qry.txt qry.dcm