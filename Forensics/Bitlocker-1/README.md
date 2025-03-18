
# Description

Jacky is not very knowledgable about the best security passwords and used a simple password to encrypt their BitLocker drive. See if you can break through the encryption!
Download the disk image here
## Hint :   
  - Hash cracking

# Write-up

Từ mô tả và hint mình cần tìm được hash của bitlock từ `disk image.dd`

## Step 1: Extract BitLocker Metadata

### Sử dụng `John the Ripper`  

![Image 1](image2.png)

Mình có được `password_hash`  

![Image 2](image3.png)  

## Step 2: Hash cracking

Sử dụng `hashcat` để crack password_hash ta có được password : `jacqueline`

![Image 3](image6.png)  

## Step 3 : giải mã ổ đĩa
Sử dụng `dislocker` để giải mã `bitlocker-1.dd` bằng `password` vừa crack được ở trên

![Image 4](image4.png)

File dislocker-file trong thư mục /mnt/bitlocker_mount là một file giải mã từ ổ đĩa BitLocker.  
Để truy xuất dữ liệu từ file này và có thể lấy được flag, cần phải mount file này để có thể truy cập vào hệ thống file của ổ đĩa đã được giải mã.  
Sử dụng kèm `-o ro (read-only)` để tránh lỗi 

![Image 5](image5.png)

Kiểm tra xem ổ đĩa đã được mount hay chưa bằng cách sử dụng lệnh `mount`  

![Image 6](image6.png)

# Flag
picoCTF{us3_b3tt3r_p4ssw0rd5_pl5!_3242adb1}


