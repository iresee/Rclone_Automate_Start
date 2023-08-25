# Rclone_Automate

Rclone开机自动挂载OneDrive

输入命令：sudo nautilus

/etc/systemd/system目录下创建rclone.service文件

把Code文件写入


说明：

#挂载为磁盘，下面的三个参数需要替换，详细看下面的说明

rclone mount DriveName:Folder LocalFolder --copy-links --no-gzip-encoding --no-check-certificate --allow-other --allow-non-empty --umask 000

#DriveName  为初始化配置填的名称

#Folder 为OneDrive里的文件夹

#LocalFolder 为VPS上的本地文件夹,如果不存在请先新建它!

例如：rclone mount Cimen:Backupload /OneDrive --copy-links --no-gzip-encoding --no-check-certificate --allow-other --allow-non-empty --umask 000

例如：rclone mount OD:/ /home/iresey/OneDrivea --copy-links --no-gzip-encoding --no-check-certificate --allow-other --allow-non-empty --umask 000

#新建本地文件夹，路径自己定，即下面的LocalFolder

mkdir /root/OneDrive

#挂载为磁盘，下面的DriveName、Folder、LocalFolder参数根据说明自行替换

参数说明:

--transfers

该参数是最大同时传输任务数量，如果经常传输大文件，或CPU性能不佳，建议设置为单线程，也就是设置为“1”

--buffer-size

该参数为读取每个文件时的内存缓冲区大小，控制rclone上传和挂载的时候的内存占用

--low-level-retries

该参数为传输文件没速度的时候重试次数，没速度的时候，单个会自动睡眠10ms起，然后再重试

如果你还涉及到读取使用，比如使用H5ai等在线播放，就在后面多加上以下三条参数:

rclone mount OD:/ /home/iresey/OneDrivea --allow-non-empty --vfs-cache-mode writes

--dir-cache-time 23h

--vfs-read-chunk-size 64M
