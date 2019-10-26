# Instalasi Metricbeat (Windows)
Diasumsikan server Elasticsearch berada di `es1.domain.net:9200` dan server kibana di `kibana1.domain.net:5601`.

## Menjalankan
1. Download dan unzip metricbeat.
2. Jalankan metricbeat: `.\metricbeat -e`

## Instalasi
1. Download dan unzip metricbeat.
```
https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-7.3.0-windows-x86_64.zip
```
2. Ubah konfigurasi `metricbeat.yml`.
* Apabila ingin menggunakan template dashboard kibana dari metricbeat:
```
setup.kibana:
  host: "kibana1.domain.net:5601"
```
* Apabila output langsung ke Elasticsearch:
```
output.elasticsearch:
  hosts: ["es1.domain.net:9200"]
```
3. **(Opsional)** Aktifkan modul tambahan. Konfigurasi awal metricbeat hanya mengumpulkan metric `system`. Misal untuk mengaktifkan modul `nginx` dan `mysql`:
```
.\metricbeat modules enable nginx mysql
```
4. Edit file konfigurasi semua modul yang aktif (misal: `.\modules.d\system.yml`).
5. **(Opsional)** Test konfigurasi dan output.
```
.\metricbeat test config -e
.\metricbeat test output
```
6. Jalankan metricbeat: `.\metricbeat -e`
7. Apabila sudah berjalan sempurna, tambah dan jalankan metricbeat sebagai service (ganti `path\to\metricbeat`):
```
sc.exe create metricbeat binpath= "path\to\metricbeat\metricbeat.exe -e -path.home path\to\metricbeat" start=delayed-auto
sc.exe start metricbeat
```

## Troubleshooting
1. **Metricbeat gagal start setelah mengaktifkan metricset tertentu.**
Beberapa metricset seperti `system.load` hanya ada pada OS tertentu.
2. **Beberapa metric tidak menampilkan nilai yang tepat di dashboard.**
Edit visualization tersebut dan ubah nilai interval dari `auto` menjadi `>=1m`. Bug ini terjadi karena interval pelaporan metricbeat lebih besar daripada interval refresh di Kibana.
2. **Dashboard melaporkan bahwa beberapa field tidak ada.**
Pastikan dashboard Kibana membaca field yang benar. Dalam suatu kasus, terjadi perubahan nama field dari `opcounters` menjadi `ops.counters`.