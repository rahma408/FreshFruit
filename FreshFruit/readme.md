## FRESHFRUIT

aplikasih ini dibuat untuk memilih buah ke dalam keranjang dan  untuk memasukan 4 buah yg di pilih kekeranjang karena hanya kita batasi 4 buah dalam 1 keranjang.cara kerjanya adalah jika kita tekan tombol aad pada gambar anggur maka akan muncul anggur di dalam keranjang begitupula seterusnya.

## HOW DOES IT WORD

-pertama fungsi dari BucketEventListener.cs berisi metode callback tunggal. Metode ini akan dipanggil  jika Tampilan yang telah didaftarkan  dipicu oleh interaksi penggunaan .

'''c#

         interface BucketEventListener
    {
        void onSucceed(string message);
        void onFailed(string message);
    }

'''

-kedua kelas diagram 

-ketiga penjelasan tentang logika yg terdapat pada aplikasiini adalah untuk memasukan buah ke keranjang dan misal kalo keranjang penuh akan ada pemberitahuan keranjang penuh.

'''c#

        public void addFruit(Fruit fruit)
        {
            if (bucketIsOverload())
            {
                eventListener.onFailed("Ops, keranjang penuh");
            }
            else
            {
                this.bucket.insert(fruit);
                eventListener.onSucceed("Yey, berhasil ditambahkan");
            }
        }

        public bool bucketIsOverload()
        {
            return bucket.countItems() >= bucket.getCapacity();
        }

        public void removeFruit(Fruit fruit)
        {
            for (int itemPosition = 0; itemPosition < bucket.countItems(); itemPosition++)
            {
                if (bucket.findAll().ElementAt(itemPosition).getName() == fruit.getName())
                {
                    bucket.remove(itemPosition);
                    eventListener.onSucceed("Yeay, Berhasil dihapus");
                }
            }
        }
        public List<Fruit> findAll()
        {
            return this.bucket.findAll();
        }

'''