# Chuyển hosting từ cPanel sang CyberPanel 

## Cách 1: 
* Tạo Full Backup từ cPanel
* Download về và upload lên VPS
* Sử dụng lệnh /usr/local/CyberCP/bin/python /usr/local/CyberCP/plogical/cPanelImporter.py --path /path/to/files để Import
* Sử dụng cat /log/file | grep Failed để kiểm tra lỗi trong quá trình restore
* Chỉnh sửa đường dẫn Document Root để đúng đường dẫn file, chỉnh sửa quyền truy cập, thay đổi phiên bản PHP
## Cách 2:
* Nén và tải Source code và sql về và up lên VPS
* Tạo website trên cyberpanel và giải nén vào thư mục tương ứng
* Tạo database và import database
* Chỉnh sửa file `.env` (laravel), `wp-config.php` (wordpress),
* Chỉnh http tự động sang https trong laravel thêm
```
  rewrite  {
    enable                  1
    autoLoadHtaccess        1
    rewriteCond %{HTTPS} !=on
    rewriteRule ^(.*)$ https://%{HTTP_HOST}%{REQUEST_URI} [R=301,L]
} vào file vhost.conf
```
