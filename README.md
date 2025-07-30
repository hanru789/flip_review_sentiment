# Flip Review Analysis

## Business Understanding
Flip adalah aplikasi keuangan yang memungkinkan pengguna melakukan transfer antar bank tanpa biaya admin, serta menyediakan berbagai fitur lain seperti pembayaran tagihan dan pembelian produk digital. Flip didirikan oleh tiga anak bangsa, yaitu Rafi Putra Arriyan, Luqman Sungkar, dan Ginanjar Ibnu Solihin. Mereka mendirikan Flip karena keresahan akan biaya transfer antar bank yang mahal pada saat itu. 
Berikut beberapa poin penting tentang Flip:
- Transfer antar bank gratis: Flip memfasilitasi transfer antar bank tanpa biaya admin, baik untuk transfer domestik maupun internasional. 
- Fitur lain: Selain transfer gratis, Flip juga menyediakan fitur untuk pembayaran tagihan, pembelian pulsa, top up e-wallet, dan transaksi lainnya. 
- Keamanan: Flip telah mengantongi izin dari Bank Indonesia dan menerapkan berbagai sistem keamanan untuk melindungi data pengguna, menurut Wikipedia. 
- Sejarah: Flip didirikan pada tahun 2016 oleh tiga alumni Universitas Indonesia dan berawal dari keresahan akan biaya transfer antar bank yang tinggi, menurut Flip.id. 
- Flip Globe: Flip juga memiliki fitur Flip Globe untuk transfer uang ke luar negeri. 
- Flip Invoice: Fitur ini membantu pengguna untuk membuat dan mengirim invoice. 
- Flip Deals: Flip Deals menawarkan berbagai penawaran menarik untuk pengguna. 

### Permasalahan Bisnis

#### Berikut adalah Permasalahan bisnis yang akan diselesaikan :
- Bagaimana rating pengguna flip.id di google play
- Adakah rating 1 yang memiliki thumbsUpCount tinggi?
- Buat model machine learning yang dapat memprediksi sentimen user dari content reviewnya


### Cakupan Proyek
Proyek ini mencakup pembuatan Dashboard interaktif dan deteksi sentiment review menggunakan model Machine Learning.

### Persiapan
Project ini menggunakan data scraping google play terhadap review applikasi flip.id. Scraping dapat dilakukan dengan menjalankan kode berikut:
```sh
!pip install google-play-scraper

from google_play_scraper import Sort, reviews
import pandas as pd

app_id = 'id.flip'

result, _ = reviews(
    app_id,
    lang='id',
    country='id',
    sort=Sort.NEWEST,
    count=10000,
    filter_score_with=None
)

df = pd.DataFrame(result)

df.to_csv('flip_review.csv', index=False)
```

Data frame hasil scraping memiliki feature sebagai berikut:

| Column name | Description |
| --- | --- |
| reviewId | review identifcation |
| userName | username of user |
| userImage | link of user image |
| content | content of review |
| score | score of review |
| thumbsUpCount | number of thumbs up to the review |
| reviewCreatedVersion | version of application that used by user |
| at | time of posting the review |
| replyContent | reply to the review content |
| repliedAt | time of reply the review |
| appVersion | curent application version |



## Business Dashboard
<image-flip_review_dashboard.png>
Dashboard dapat diakses meggunakan link berikut:
 https://public.tableau.com/views/FlipReview/Dashboard1?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link&:device=desktop


## Conclusion
- User dapat menggunakan dashboard interaktif untuk melakukan analisa mendalam terhadap review yang  diberikan oleh pengguna aplikasi.
- Model machine learning yang dihasilkan memiliki score f1 91 persen yang mana ini sudah cukup baik untuk menlakukan predksi sentimen dari review applikasi.
