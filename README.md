~~ Apache Spark ~~

Pertama yang saya siapkan adalah VM untuk proses pengerjaan disini saya memakai Alibaba Cloud dengan nama VM faris-185410047 yang sedang berjalan
 
VM yang telah saya buat akan saya remote dengan putty karena saya menggunakan OS Windows. Pada putty isikan IP public VM lalu login menggunakan root atau username kemudian isi password yang benar. Setelah bisa masuk maka akan muncul seperti gambar berikut.
 
Setelah masuk remote VM pertama yang dilakukan adalah update pada Ubuntu 18.04 komponennya di VM saya
 
Kemudian install yang diperlukan dalam proses seperti jdk seperti berikut, karena nanti akan perlu java dalam menjalankan proses-proses selanjutnya
 
Setelah diinstal maka dicek versi java yang terinstal, disini openjdk versi 11.0.9.1
 
Kemudian disini lanjut menggunakan perintah curl untuk mendownload berupa link, yang didownload adalah apache spark versi 2.4.7
 
Kemudian diekstrak hasil download apache spark akan menampilkan banyak sekali data yang terekstrak
 
Setelah diekstrak maka direktori yang telah diekstrak dipindah ke direktori /opt/spark
 
Setelah dipindahkan maka masuk direktori /opt/spark , pada bagian ini menjalankan perintah untuk menjalankan apache sparknya, terlihat ada tulisan starting org.apache.spark
 
Untuk mengecek apakah apache spark memiliki akses port 8080 dengan perintah seperti gambar berikut. Terlihat java sudah memiliki aksesnya
 
Disini melihat log yang sedang berjalan pada apache spark dengan menjalankan cat pada file spark-root-org.apache.spark.deploy.master.Master-l-(id atau nama vm).out
  
Kemudian disini dijalankan lagi apache spark dengan url berupa spark testing, maka muncul output starting apache spark worker
 
Selanjutnya pada direktori /opt/spark buat file baru bernama input.txt
 
Dari kata-kata yang sudah saya siapkan disini yang akan dihitung perkatanya, pada notepad ini saya copy nantinya ke dalam editor pico putty
 
Pada putty masih didalam pico input.txt tinggal pastekan disini lalu save
 
Disini masuk ke spark shell atau istilahnya terminalnya milik apache spark, maka akan muncul welcome to spark, dan scala> disini tempat untuk menjalankan perintah-perintah apache spark
 
Perintah berikut ini adalah untuk mendeklarasikan input.txt adalah source file yang akan diproses nantinya, dan diklarasikan sebagai inputfile
 
Disini dilakukan deklarasi pada counts yang berartikan penghitungan banyak kata pada inputfile (yaitu file input.txt) dengan beberapa perintah seperti line.split, map, reduceByKey
 
 
Kemudian dilakukan cache pada counts akan menampilkan bahwa data input.txt sudah diproses atau sudah dilakukan penghitungan
 
Pada bagian saveAsTextFile(“output”) berarti melakukan save hasil pada direktori output didalam direktori /opt/spark ada direktori baru yang dibuat bernama output
 
Masuk ke direktori output untuk nantinya menjalankan/menampilkan hasil hitung/proses
 
Dengan perintah cat pada part-00000 maka muncul hasilnya seperti 3 gambar berikut, jika ada kata yang sama maka dihitung sesuai banyak katanya disebelah kanan kata, seperti yang sudah diset pada val counts di scala> sebelumnya sudah terlihat format tampilannya
