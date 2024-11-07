# install-centos8


## FIX Problem
```
Errors during downloading metadata for repository 'extras':
  - Curl error (6): Couldn't resolve host name for http://mirrorlist.centos.org/?release=8&arch=x86_64&repo=extras&infra=stock [Could not resolve host: mirrorlist.centos.org]
Error: Failed to download metadata for repo 'extras': Cannot prepare internal mirrorlist: Curl error (6): Couldn't resolve host name for http://mirrorlist.centos.org/?release=8&arch=x86_64&repo=extras&infra=stock [Could not resolve host: mirrorlist.centos.org]
```
ให้ทำการแก้ไขไฟล์ `/etc/yum.repos.d/CentOS-Base.repo` โดยใส่คำสั่งต่อไปนี้
```bash
nano /etc/yum.repos.d/CentOS-Base.repo
```

```bash
[baseos]
name=CentOS-8 - BaseOS
baseurl=http://vault.centos.org/8.5.2111/BaseOS/x86_64/os/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[appstream]
name=CentOS-8 - AppStream
baseurl=http://vault.centos.org/8.5.2111/AppStream/x86_64/os/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial

[extras]
name=CentOS-8 - Extras
baseurl=http://vault.centos.org/8.5.2111/extras/x86_64/os/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-centosofficial
```
จากนั้น run คำสั่ง
```bash
sudo yum clean all
sudo yum makecache
```
