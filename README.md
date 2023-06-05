# Mongodb-Cluster-Replication

- Amazon Linux-2 server için "install-mongodb.md" dosyasından mongodb 4.4 kurulumu yapılır.

(https://www.mongodb.com/docs/v4.4/tutorial/install-mongodb-on-amazon/)


- Replica set kurulumu (mongodb cluster oluşturmak için) "install-mongodb.md" dosyasından yapılır.

(https://www.mongodb.com/docs/v4.4/tutorial/convert-standalone-to-replica-set/)


- Bütün serverlara girilerek gerekli konfigürasyonlar yapılır.


- Mongodb ye yazılan dataları özel bir EBS de tutmak için AWS konsolda her server için yeni bir EBS volume oluşturulup serverlara attach edilir.

- mongodb-added-new-ebs.md dosyasında olan komutlar koşularak kurulum yapılır.
