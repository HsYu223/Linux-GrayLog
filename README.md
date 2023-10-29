# Linux-GrayLog

安裝 mongodb
```shell
sudo rpm -ivh mongodb-org-server-5.0.14-1.el8.x86_64.rpm
sudo rpm -ivh mongodb-org-shell-5.0.14-1.el8.x86_64.rpm
sudo rpm -ivh mongodb-org-mongos-5.0.14-1.el8.x86_64.rpm
```

修改mongod.conf
```shell
sudo vi /etc/mongod.conf
```

連線設定mongodb
```shell
# 建立連線
mongo 127.0.0.1:27017

# 查詢狀態
rs.status()

# 伺服器初始化
rs.initiate()

# 設定叢集主機連線
config = { "_id": "{replName}", "members": [{"_id":0,"host":"{host1:port}"},{"_id":1,"host":"{host2:port}"},{"_id":2,"host":"{host3:port}"}] }
rs.config()(config)
```

設定資料儲存資料夾權限
```shell
sudo sudo chown -R mongod:mongod /elasticsearch/mongodb
```

啟動服務
```shell
sudo systemctl start mongod
sudo systemctl status mongod
sudo systemctl enable mongod
```

安裝 mongodb
```shell
sudo rpm -ivh elasticsearch-7.10.2-x86_64.rpm
```

修改
```shell
sudo vi /etc/elasticsearch/elasticsearch.yml
```

啟動服務
```shell
sudo systemctl enable elasticsearch
sudo systemctl start elasticsearch
sudo systemctl status elasticsearch
```

確認叢集狀態
```shell
curl -XGET 'http://127.0.0.1:9200/_cluster/health?pretty=true'
```

安裝graylog
```shell
sudo rpm -ivh pwgen-2.08-1.el7.x86_64.rpm
rpm -ivh graylog-server-5.1.3-1.x86_64.rpm
sudo rpm -ivh graylog-server-5.1.3-1.x86_64.rpm
```

設定密碼
```shell
sudo pwgen -N 1 -s 96
echo -n {自訂密碼} | sha256sum
```

修改啟動設定
```shell
sudo vi /etc/graylog/server/server.conf
```

啟動服務
```shell
sudo systemctl enable graylog-server.service
sudo systemctl start graylog-server.service
sudo systemctl status graylog-server.service
```
