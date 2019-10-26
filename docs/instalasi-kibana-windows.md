# Instalasi Kibana (Windows)
Diasumsikan server Kibana akan berada di `kibana1.domain.net:5601`.

## Menjalankan
1. Download dan unzip Kibana.
2. Jalankan Kibana: `.\bin\kibana.bat`
3. Browse: `http://kibana1.domain.net:5601/`

## Instalasi
1. Download dan unzip Kibana.
```
https://artifacts.elastic.co/downloads/kibana/kibana-7.3.0-windows-x86_64.zip
```
2. 
3. Jalankan Kibana: `.\bin\kibana.bat`
4. Browse: `http://kibana1.domain.net:5601/`
5. Apabila sudah berjalan sempurna, tambah dan jalankan Kibana sebagai service:
```
sc.exe create kibana binpath= "path\to\metricbeat\metricbeat.exe -e -path.home path\to\metricbeat" start=delayed-auto
sc.exe start kibana
```

## Troubleshooting