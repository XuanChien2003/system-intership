# Liệt kê tất cả service
Kiểm tra tất cả service có trên hệ thống với câu lệnh:
```
systemctl list-unit-files --type service -all
```
  ![altimage](../5.Lab/Img/Systemd1.png)

# 1. Kiểm tra trạng thái
```
systemctl status systemd-boot-check-no-failures.service
```
![altimage](../5.Lab/Img/Systemd2.png)

# 2. Start service
```
sudo systemctl start systemd-boot-check-no-failures.service
```
## Kiểm tra lại:
```
systemctl status systemd-boot-check-no-failures.service
```
![altimage](../5.Lab/Img/Systemd3.png)

# 3. Stop service
```
sudo systemctl stop systemd-boot-check-no-failures.service
```
## Kiểm tra lại:
```
systemctl status systemd-boot-check-no-failures.service
```
![altimage](../5.Lab/Img/Systemd4.png)

# 4. Enable service
```
sudo systemctl enable systemd-boot-check-no-failures.service
```
## Kiểm tra lại:
```
systemctl is-enabled systemd-boot-check-no-failures.service
```
![altimage](../5.Lab/Img/Systemd5.png)

# 5. Disable service
```
sudo systemctl disable systemd-boot-check-no-failures.service
```
## Kiểm tra lại:
```
systemctl is-enabled systemd-boot-check-no-failures.service
```
![altimage](../5.Lab/Img/Systemd6.png)

<!-- # 7. Xem log service -->
# 6. Xem log service

![altimage](../5.Lab/Img/Systemd7.png)

