# Instalasi Elasticsearch (Windows)
Diasumsikan server Elasticsearch akan berada di `es1.domain.net:9200`.

## Menjalankan
1. Download dan unzip Elasticsearch.
2. Jalankan Elasticsearch: `.\bin\elasticsearch.bat`
3. Test output menggunakan PowerShell:
```
PS > Invoke-RestMethod http://es1.domain.net:9200
```

## Instalasi
1. Download dan unzip Elasticsearch.
```
https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.3.0-windows-x86_64.zip
```
2. Ubah `.\config\elasticsearch.yml`:
```
cluster.name: es-cluster
node.name: es1.domain.net
network.host: _site_
bootstrap.memory_lock: true
# Uncomment apabila cluster hanya terdiri dari satu node. 
#discovery.type: single-node
# Uncomment apabila data Elasticsearch akan disebar di beberapa disk.
#path.data: C:\path\to\data, D:\path\to\data
```
* **(Opsional)** Ubah `.\config\jvm.options` agar menggunakan heap space 4gb:
```
-Xms4g
-Xmx4g
```
3. Jalankan Elasticsearch: `.\bin\elasticsearch.bat`
4. Test output menggunakan PowerShell:
```
PS > Invoke-RestMethod http://es1.domain.net:9200
```
6. Apabila sudah berjalan sempurna, tambah dan jalankan Elasticsearch sebagai service:
```
.\bin\elasticsearch-service install
.\bin\elasticsearch-service start
```

## Troubleshooting