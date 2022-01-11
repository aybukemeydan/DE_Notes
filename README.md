# KURULUMLAR

## Windows için Docker Kurulumu (Windows 11 ve üzeri sürümler için)

*Windows sürümünüzü run ile winver yazarak öğrenebilirsiniz*


### WSL Kurulumu
Docker'ın Windows bir bilgisayarda çalışabilmesi için ilk başta wsl (windows subsystem for linux) kurulumu yapılmalıdır.

Microsoft Store'dan Ubuntu indirilir.

Windows PowerShell yönetici olarak çalıştırılır ve şu komut yazılır.

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Sırasıyla;
```
wsl --update
```

```
wsl --shutdown
```

```
wsl --set-default-version 2
```

Linux kernelini indirdik Ubuntu kurulumunu da komutla yapabiliriz.
```
wsl --install -d Ubuntu
```
Bu komut sonrası Ubuntu terminali kendiliğinden açılıyor,açılmazsa bilgisayar aç\kapa önerilir. Ubuntu terminali kullanıcı adı ve şifre belirtmenizi istiyor. Sonrasında disk alanını öğrenmek için şu komutu girebilirsiniz:
```
df -h
```
Ubuntu çalışıyor mu diye kontrol etmek için:
```
wsl -l -v
```
WSL için kurulum tamam.

### Docker Kurulumu

[Docker'ın sayfasından](https://www.docker.com/products/docker-desktop) ilk başta uygulamayı indirelim. Kurulum tamamlandıktan sonra Docker Desktop'u açalım. Çalışıp çalışmadığını yine yukarıda kullandığımız ```wsl -l -v``` ile kontrol edebiliriz.

Setting > Resources'tan WSL Integration'a gelip Ubuntu'yu seçeceğiz ama seçmeden önce ```wsl -l``` ile Ubuntu(default) şeklinde mi geliyor kontolü yapılmalı.

Windows Shell ile konteynırları run edebiliriz artık.

#### Örnek

İlk hello world containerımızı çalıştıralım.

```docker run hello-world```

Container'ı ilk lokal olarak arıyor bulamayınca [DockerHub](https://hub.docker.com/search?type=image) üzerinden indiriyor.

Çalışan konteynırları görüntülemek için;
```
docker ps -a
```
Çalışan bir konteynırı durdurmak için;
```
docker stop containerID
```
Burada containerID'yi çalışan konteynırları görüntülerken görmüştük. İlk 3 karakterini yazsak dahi durduracaktır.

Kaldırmak istiyorsak;
```
docker rm containerID``` ile komut satırları aracılığıyla ya da Docker Desktop üzerinden manuel bir şekilde bu işlemleri yapabilirsiniz.




