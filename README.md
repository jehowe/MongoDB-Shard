# MongoDB-Shard
This MongoDB is shard cluster that has been deployed on docker

Connect mongors1n1 to replica

echo 'rs.initiate(); sleep(1000); cfg = rs.conf(); cfg.members[0].host = "ACA-MongoDB_mongors1n1_1"; rs.reconfig(cfg); rs.add("ACA-MongoDB_mongors1n2_1"); rs.add("ACA-MongoDB_mongors1n3_1"); rs.status();' | mongo

Connect mongors2n1 to replica

echo 'rs.initiate(); sleep(1000); cfg = rs.conf(); cfg.members[0].host = "ACA-MongoDB_mongors2n1_1"; rs.reconfig(cfg); rs.add("ACA-MongoDB_mongors2n2_1"); rs.add("ACA-MongoDB_mongors2n3_1"); rs.status();' | mongo

Connect mongos1 to mongors1n1 and mongors2n1

Shell>mongo

mongo>sh.addShard('mongors1/ACA-MongoDB_mongors1n1_1:27017');

mongo>sh.addShard('mongors2/ACA-MongoDB_mongors2n1_1:27017'); 
