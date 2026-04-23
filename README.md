# A.R.O.G VPN

Kendi Oracle sunucuna bağlanan, Windows için GUI VPN istemcisi.

## Dosya Yapısı

```
AROG_VPN/
├── src/
│   ├── main.cpp      ← Ana pencere ve GUI
│   ├── arog.h        ← VPN bağlantı sınıfı
│   ├── setup.h       ← Ayarlar dialog'u
│   ├── arog.rc       ← Resource (dialog + versiyon)
│   └── resource.h    ← Resource ID'leri
├── server/
│   ├── setup_server.sh   ← Oracle'da bir kez çalıştır
│   └── add_client.sh     ← Her yeni kullanıcı için
└── .github/workflows/
    └── build.yml         ← GitHub Actions otomatik build
```

## Kurulum Adımları

### 1. Oracle Sunucu Kur
```bash
ssh ubuntu@SUNUCU_IP
bash setup_server.sh
```
Script sona erince sana **Sunucu Public Key** ve **Sunucu IP** verir.

### 2. Client Key Üret
```bash
bash add_client.sh
```
Sana **Client Private Key** ve **Client IP** verir.

### 3. AROG VPN EXE'yi Build Et
- Bu repoyu GitHub'a push et
- Actions sekmesinden build otomatik başlar
- Artifacts'tan `AROG_VPN.exe` indir

### 4. EXE'yi Çalıştır
1. `AROG_VPN.exe` çalıştır
2. İlk açılışta ayar ekranı gelir
3. Sunucu IP, Sunucu Public Key, Client Private Key gir
4. **BAĞLAN** butonuna bas

## Gereksinimler (İstemci PC)
- Windows 10/11
- [WireGuard](https://www.wireguard.com/install/) yüklü olmalı

## Notlar
- Config `C:\AROG\arog.conf` dosyasına kaydedilir
- WireGuard tunnel servisi olarak çalışır
- Bağlantı kesilince tunnel kaldırılır
