# TIA Portal - PLCSIM Periyodik Sag Sol           	 Calistirma

Sağa ve sola çalışabilen motorun periyodik olarak çalıştırılmasının programlanması. Tia portal üzerinden ladder diyagramı çizilmiş, plcsim den simülasyonu sağlanmıştır.

**not:** Tiaportal ve plcsim versiyon16 sı üzerinden oluşturulmuştur. 

 - Motor ilk başta sağ yönde çalışacaktır.
 - Sağa doğru çalıştıktan 10sn sonra motorun sağa dönme işlemi duracaktır.
 - Sağ motor durduktan sonra 6sn boyunca motor duruk kalacaktır. 
 - 6sn sonunda motor sola doğru çalışmaya başlayacaktır.
 - Motorun sola doğru çalışması 10sn sürecektir. 10 saniye sonunda sola motor duracaktır. 
 - sola motor durduktan sonra 6 saniyelik bekleme yapacaktır.
 - Bu beklemenin sonrasında işlem tekrar başa dönecektir. 
 

## Açıklamalar
### Projem için oluşturduğum taglar şu şekildedir:
![enter image description here](https://github.com/hrngcmn/TiaPortal_plcsim_periyodik_sag_sol_calistirma/blob/main/plc_tags_foto.png?raw=true)

### Ladder diyagramlarının oluşturulması:
* **network1** ve **network2** de sistemin açılıp kapanmasının kontrolünü sağlayacak olan yardımcı rölenin set - reset edilmesi durumu gösterilmektedir. 

![enter image description here](https://github.com/hrngcmn/TiaPortal_plcsim_periyodik_sag_sol_calistirma/blob/main/nw1_nw2_foto.png?raw=true)

* **Network3** te starta basılınca set olan yardımcı rölenin kontak kapatması ile beraber sağ motorun çalışması ve beraberinde 10sn lik sayıcı çalıştırmasını sağlanmıştır. Q0.1 kapalı kontağı elektriksel mühürleme işlemi yapmaktadır.  bekle1 kapalı kontaklı rölesi 10sn sonunda açılacaktır, bu durum 10 sn sonunda sağ motorun kapanmasını sağlar.
* **Network4** bekle 1 düz zaman rölesinin 10 sn saymasından sonra açılması ve beraberinde 6 sn lik gecikme oluşturması sağlanmıştır. 

![enter image description here](https://github.com/hrngcmn/TiaPortal_plcsim_periyodik_sag_sol_calistirma/blob/main/nw3_nw4_foto.png?raw=true)

**network5** te sol motorun çalışma işlemi kontrol edilmiştir. bekle2 düz zaman rölesinin 6sn saymasından sonra açık olan kontağı kapanacaktır. bu sayede sol motor aktif olacak ve bekle3 zaman rölesi saymaya başlayacaktır. bekle3 10sn saydıktan sonra sol motoru durduracaktır.
**network6** kapanan bekle3 kontağı bekle4 zaman rölesini çalıştırmaya başlayacaktır. Bekle 4 zaman rölesi sol motor durduktan sonra 6 sn sayması için gereklidir. Bekle4 zaman rölesi 6sn saydıktan sonra zaman rölesinin kontakları yer değiştirecektir. Bu değişme bütün zaman rölelerinin enerjisini bir anda kesecektir. TON tipi zaman rölesinin enerjisinin kesilmesi durumunda tüm kontaklarını ilk haldeki durumunu alır. İşte bu sayede sistemin periyodikliği sağlanmış olur.  ![enter image description here](https://github.com/hrngcmn/TiaPortal_plcsim_periyodik_sag_sol_calistirma/blob/main/nw5_nw6_foto.png?raw=true)
