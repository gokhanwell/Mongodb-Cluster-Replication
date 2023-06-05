#create a "/etc/yum.repos.d/mongodb-org-4.4.repo" file

      sudo vi /etc/yum.repos.d/mongodb-org-4.4.repo
-
      [mongodb-org-4.4]
      name=MongoDB Repository
      baseurl=https://repo.mongodb.org/yum/amazon/2/mongodb-org/4.4/x86_64/
      gpgcheck=1
      enabled=1
      gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc


#install mongodb with yum package 

      sudo yum install -y mongodb-org

      sudo systemctl start mongod

      sudo systemctl status mongod

      sudo systemctl enable mongod


#configure mongodb
      
      sudo vi /etc/mongod.conf

#added and edited following parameter  #enable replica set 

      net:
        port: 27017
        bindIp:  "xx.xx.xx.xx" # This must be changed as per the private ip of the ec2

      replication:
        replSetName: "mongo-replica" #This must be same in all mongod.conf file in replica mongo servers

-
      sudo systemctl restart mongod


#define hostname each servers

      hostnamectl set-hostname mongo-1   #first server  e.g.
      hostnamectl set-hostname mongo-2   #second server  e.g.
      hostnamectl set-hostname mongo-3   #third server  e.g.

#define mongo hostname all servers /etc/hosts

      sudo vi /etc/hosts 
-
      "mongo-1-private-ip"  mongo-1
      "mongo-2-private-ip"  mongo-2
      "mongo-3-private-ip"  mongo-3


#Connect to mongodb from any server

      mongo --host mongo-1

-
      rs.initiate(
         {
            _id: "mongo-replica",
            version: 1,
            members: [
               { _id: 0, host : "mongo-1:27017" },
               { _id: 1, host : "mongo-2:27017" },
               { _id: 2, host : "mongo-3:27017" }
            ]
         }
      )

check the status "rs.status()" with this command.
