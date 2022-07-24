# STRIDE-NODE-TESTNET
Cosmos ekosisteminden, kısa sürede bitecek olan, kolay kurulum herkesin katılması gereken ödüllü Stride Node testneti.

**Stride Özet İnceleme**

Cosmos ekosistemindeki mevcut DeFi durumu yetersiz ve verimsiz. Kullanıcılar, tokenlerini pasif getiri için stake etmek veya DeFi'ye katılmak arasında bir tercih yapmak zorunda kalıyor ve kendilerini daha fazla getiri için daha fazla riske maruz bırakıyor.Stride, kullanıcıların varlıklarını herhangi bir Cosmos zincirinde liquid staking etmelerine izin verecek.


![stride](https://user-images.githubusercontent.com/98783018/180624535-13dcf1b6-03b1-42d2-a42c-6e9a7ea0bfcf.jpg)

**Not:** Cosmos ekosisteminde benim bildiğim bunu yapacak olan ilk proje. Katılın kolay kurulumu var ve ayrıca kısa sürede bitecek

Başlangıç: 25/06/2022

Bitiş: TBA

Gelişmeleri Takip Etmek Ve Yardım Almak İçin Telegram:https://t.me/LossNode

Video:https://youtu.be/SLSZi48ZssE

**Sistem Gereksinimleri**

Ekibin önerdiği
```
4x CPU
32GB RAM
200GB of storage (SSD or NVME)
```
**Benim gücüm buna yetti**
```
4 CPU
8 RAM
200 GB SSD
```

Less Goo 🚀

Otomatik Kurulum Komutunu Girelim

```
wget -q -O stride.sh https://raw.githubusercontent.com/AKnode/rekapan-node/main/stride/stride.sh && chmod +x stride.sh && sudo /bin/bash stride.sh
```

Kurulumdan sonra bu komutu giriyoruz

```
source $HOME/.bash_profile
```
Loglar akıyor mu bakalım

```
sudo journalctl -u strided -f --no-hostname -o cat
```

Sync Durum Kontrol Komutu (False olmasını bekle validatör kurmak için)

```
strided status 2>&1 | jq .SyncInfo
```
Node bilgisi

```
strided status 2>&1 | jq .NodeInfo
```
Validatör bilgisi

```
strided status 2>&1 | jq .ValidatorInfo
```
Cüzdan Oluşturma Komutu
```
strided keys add $WALLET
```
Eski cüzdanı geri getirme

```
strided keys add $WALLET --recover
```
Cüzdan bakiyesi sorgulama

```
strided query bank balances $STRIDE_WALLET_ADDRESS
```

Cüzdanı oluşturduktan sonra Discorda gidip test token talep edelim

Discord Link:https://discord.gg/xqgBmNaq

Faucet e şöyle yazıyoruz: $faucet-stride:cüzdanadresi
![token talep etme](https://user-images.githubusercontent.com/98783018/180625048-11471c22-5ce3-486d-a0a8-f7f6176c664a.png)

Node'umuz Sycn olduysa şimdi validatör kurabiliriz

Sync Durum Kontrol Komutu (False olmasını bekle validatör kurmak için)
```
strided status 2>&1 | jq .SyncInfo
```

Validatör oluşturma

```
strided tx staking create-validator \
  --amount 10000000ustrd \
  --from cüzdanismi \
  --commission-max-change-rate "0.01" \
  --commission-max-rate "0.2" \
  --commission-rate "0.07" \
  --min-self-delegation "1" \
  --pubkey  $(strided tendermint show-validator) \
  --moniker monikerismi \
  --chain-id $STRIDE_CHAIN_ID
```

**Explorer:**
https://stride.explorers.guru/validators

_**Sosyal Medya Hesaplarımız**_

📲 https://linktr.ee/lossnode

Translate ettim kendime ait bir script değildir.
