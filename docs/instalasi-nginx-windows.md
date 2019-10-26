# Instalasi nginx (Windows)
Diasumsikan server nginx berada di `nginx.domain.net`.

## Menjalankan
1. Download dan unzip nginx.
2. Jalankan nginx: `.\nginx`
3. Browse: `http://nginx.domain.net/`

## Instalasi
1. Download dan unzip nginx.
```
http://nginx.org/download/nginx-1.16.1.zip
```
2. Ubah konfigurasi `.\conf\nginx.conf`. Lihat **Template Konfigurasi**.
3. Jalankan nginx: `.\nginx`
4. Browse: `http://nginx.domain.net/`
5. (Opsional) Apabila sudah berjalan sempurna, tambah dan jalankan nginx sebagai service (menggunakan nssm, https://nssm.cc/download):
```
cd path\to\nssm
.\nssm install nginx "path\to\nginx\nginx.exe"
.\nssm set nginx Start SERVICE_AUTO_START
sc.exe start nginx
```

## Template Konfigurasi

## Troubleshooting