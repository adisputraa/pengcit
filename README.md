
# Word Segmentation

# A. Grayscale
Grayscale adalah sebuah representasi dari gambar atau citra yang menggunakan skala keabuan. Dalam skala keabuan, setiap piksel pada gambar memiliki nilai kecerahan tunggal yang berkisar antara 0 (hitam) hingga 255 (putih). Citra grayscale tidak memiliki komponen warna seperti pada citra berwarna (RGB).

Teori grayscale meliputi langkah-langkah konversi gambar berwarna menjadi grayscale:

## 1. Representasi Warna RGB:
   Gambar berwarna biasanya direpresentasikan dalam format RGB (Red, Green, Blue). Setiap piksel pada gambar memiliki tiga komponen warna, yaitu merah (R), hijau (G), dan biru (B). Setiap komponen warna ini memiliki nilai intensitas yang berkisar antara 0 hingga 255.

## 2. Konversi ke Grayscale:
   Konversi gambar berwarna ke citra grayscale melibatkan perhitungan nilai kecerahan piksel baru berdasarkan komponen warna RGB. Terdapat beberapa metode yang umum digunakan dalam konversi ke grayscale, di antaranya:
   - Metode Rata-rata (Average Method): Nilai kecerahan piksel grayscale dihitung sebagai rata-rata dari nilai intensitas ketiga komponen warna RGB. Misalnya, jika nilai intensitas R, G, dan B adalah (r, g, b), maka nilai kecerahan piksel grayscale (L) dapat dihitung sebagai berikut: L = (r + g + b) / 3.
   - Metode Bobot (Weighted Method): Metode ini memberikan bobot yang berbeda untuk setiap komponen warna RGB. Misalnya, bobot yang umum digunakan adalah 0.2989 untuk R, 0.5870 untuk G, dan 0.1140 untuk B. Nilai kecerahan piksel grayscale (L) dihitung sebagai: L = 0.2989 * R + 0.5870 * G + 0.1140 * B.
   - Metode Luminance (YUV Method): Metode ini menggunakan transformasi warna YUV, di mana komponen Y (Luminance) adalah representasi kecerahan piksel grayscale. Nilai Y dihitung berdasarkan persamaan matematis yang kompleks dan melibatkan konversi ke ruang warna YUV.

## 3. Representasi Grayscale:
   Setelah konversi ke grayscale, setiap piksel pada gambar hanya memiliki satu komponen warna tunggal yang mewakili tingkat kecerahan. Nilai kecerahan ini biasanya merupakan bilangan bulat antara 0 hingga 255, di mana 0 mewakili hitam dan 255 mewakili putih.

Keuntungan dari penggunaan citra grayscale dalam pengolahan citra adalah:
- Memperkecil kompleksitas pemrosesan karena hanya terdapat satu komponen warna.
- Mengurangi penggunaan memori dan ruang penyimpanan karena hanya perlu menyimpan satu saluran warna.
- Memudahkan dalam pengolahan citra seperti filtering, segmentasi, dan analisis tekstur.

Penting untuk dicatat bahwa konversi ke grayscale menghilangkan informasi warna dari gambar asli. Oleh karena itu, dalam beberapa kasus, seperti pengenalan objek berwarna atau analisis warna, citra berwarna mungkin lebih diinginkan daripada citra grayscale.

# B.Thresholding dan Dilasi

## 1. Thresholding:
   Thresholding adalah proses mengubah citra menjadi citra biner dengan membaginya menjadi dua nilai intensitas, yaitu nilai ambang bawah (threshold) dan nilai ambang atas. Setiap piksel pada citra akan dibandingkan dengan nilai ambang. Jika nilai piksel di bawah ambang, piksel tersebut akan diubah menjadi hitam (0), sedangkan jika nilainya di atas ambang, piksel akan diubah menjadi putih (255) atau sebaliknya, tergantung pada metode thresholding yang digunakan.

   Terdapat beberapa metode thresholding yang umum digunakan, di antaranya:
   - Binary Thresholding: Semua piksel dengan intensitas di bawah ambang akan diubah menjadi hitam (0), dan piksel dengan intensitas di atas ambang akan diubah menjadi putih (255).
   - Adaptive Thresholding: Ambang yang digunakan berbeda-beda untuk setiap piksel, yang ditentukan berdasarkan karakteristik lokal piksel tersebut.
   - Otsu's Thresholding: Metode yang memilih nilai ambang secara otomatis berdasarkan analisis histogram citra.

   Penggunaan thresholding sangat umum dalam segmentasi citra, di mana objek diinginkan untuk dipisahkan dari latar belakangnya. Dengan mengubah citra menjadi citra biner, kita dapat mengidentifikasi objek berdasarkan perbedaan intensitasnya dengan latar belakang.

## 2. Dilasi:
   Dilasi adalah operasi morfologi yang digunakan untuk memperluas atau memperbesar area objek pada citra biner. Operasi ini melibatkan elemen struktural, yang biasanya berbentuk kotak atau lingkaran, dan akan digeser melintasi citra.

   Pada setiap posisi elemen struktural, dilasi akan mengubah piksel tengah menjadi piksel putih (255) jika setidaknya satu piksel dalam elemen struktural adalah piksel putih. Hal ini mengakibatkan objek pada citra biner menjadi lebih tebal dan terhubung.

   Dilasi berguna dalam mengisi lubang pada objek, menghubungkan objek yang terputus, memperbaiki kontur objek yang kasar, dan memperluas ukuran objek dalam citra biner.

   Prinsip dilasi adalah menjalankan elemen struktural pada setiap piksel dalam citra dan mengubah piksel tengah sesuai dengan aturan yang telah ditentukan. Misalnya, jika ada piksel putih dalam elemen struktural, piksel tengah akan diubah menjadi putih.

   Penggunaan dilasi sering terjadi bersama dengan operasi morfologi lainnya, seperti erosi, untuk mencapai hasil yang diinginkan dalam pemrosesan citra.

# C. Kontur

Kontur adalah representasi visual dari tepi objek dalam citra. Dalam pengolahan citra, kontur digunakan untuk mengidentifikasi dan memisahkan objek dari latar belakangnya. Kontur mencakup garis yang menghubungkan piksel-piksel dengan intensitas yang berbeda di sekitar objek.

Konsep penting terkait kontur:

## 1. Deteksi Kontur:
   Deteksi kontur adalah proses menemukan garis-garis atau kurva yang merepresentasikan tepi objek dalam citra. Ada beberapa metode yang umum digunakan untuk mendeteksi kontur, di antaranya:
   - Metode Gradient: Metode ini berdasarkan perbedaan intensitas antara piksel-piksel tetangga. Perubahan tajam dalam intensitas dianggap sebagai indikasi adanya tepi atau kontur.
   - Metode Thresholding: Metode ini mengubah citra menjadi citra biner dan mengidentifikasi tepi objek sebagai perbedaan intensitas antara objek dan latar belakang.
   - Metode Canny: Metode ini menggunakan filter Gaussian untuk menghilangkan noise dan kemudian mendeteksi tepi dengan memanfaatkan gradien intensitas.

## 2. Sifat Kontur:
   Kontur memiliki beberapa sifat yang berguna dalam analisis dan pengolahan citra, di antaranya:
   - Panjang Kontur: Mengukur panjang total dari garis yang membentuk kontur objek.
   - Luas Kontur: Mengukur luas area yang dikelilingi oleh kontur objek.
   - Keliling Kontur: Mengukur total panjang tepi dari kontur objek.
   - Titik Tengah: Menunjukkan pusat massa atau titik tengah dari kontur objek.
   - Convex Hull: Merupakan himpunan dari semua titik yang mencakup kontur objek.

## 3. Hierarki Kontur:
   Dalam citra dengan objek yang saling berhubungan, kontur dapat memiliki hubungan hierarkis. Hierarki kontur menggambarkan relasi antara kontur utama (kontur luar) dan kontur anak (kontur dalam). Ini memungkinkan penggolongan dan pengelompokan objek dalam citra.

## 4. Penggunaan Kontur:
   Kontur memiliki berbagai aplikasi dalam pengolahan citra, di antaranya:
   - Segmentasi Objek: Kontur digunakan untuk memisahkan objek dari latar belakangnya dalam proses segmentasi.
   - Pengenalan dan Klasifikasi Objek: Dengan menganalisis bentuk dan karakteristik kontur, objek dapat dikenali dan diklasifikasikan ke dalam kategori tertentu.
   - Deteksi Pergerakan: Dalam aplikasi pengawasan atau pengenalan gerakan, kontur digunakan untuk mendeteksi perubahan posisi atau pergerakan objek dalam citra berurutan.

Pemahaman tentang kontur dan penggunaannya sangat penting dalam pengolahan citra. Dengan mengidentifikasi dan menganalisis kontur, kita dapat memperoleh informasi yang berguna tentang objek dalam citra dan mengambil tindakan yang diperlukan sesuai dengan kebutuhan aplikasi yang sedang digunakan.
## Langah peyelesaian Kodingan

img = cv2.imread(image_path)            
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

Langkah pertama adalah membaca gambar dari path yang diberikan dan mengubah format warna gambar menjadi RGB. Ini penting karena OpenCV secara default membaca gambar dalam format BGR.

img_gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)  
Gambar yang telah diubah ke format RGB kemudian dikonversi menjadi grayscale. Konversi ini berguna untuk mempermudah proses pengolahan citra selanjutnya.

_, thresh = cv2.threshold(img_gray, 120, 255, cv2.THRESH_BINARY_INV)  
kernel = np.ones((3, 10), np.uint8)  
dilated = cv2.dilate(thresh, kernel, iterations=1)

Thresholding digunakan untuk mengubah citra grayscale menjadi citra biner, di mana piksel di atas nilai ambang batas akan diubah menjadi putih (255) dan piksel di bawah nilai ambang batas akan diubah menjadi hitam (0). Selanjutnya, dilasi dilakukan untuk memperluas area piksel putih dan menghubungkan karakter-karakter yang saling berdekatan.

contours, _ = cv2.findContours(dilated.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)  
sorted_contours_lines = sorted(contours, key=lambda ctr: cv2.boundingRect(ctr)[1])

Dalam langkah ini, dilakukan pencarian kontur pada citra hasil dilasi dan kontur-kontur tersebut diurutkan berdasarkan posisi vertikal mereka (garis-garis). Hal ini dilakukan untuk memisahkan karakter-karakter pada setiap baris teks.

for line in sorted_contours_lines:     
    # ...
    cnt, _ = cv2.findContours(roi_line.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)
    sorted_contour_words = sorted(cnt, key=lambda cntr: cv2.boundingRect(cntr)[0])
    # ...
    for word in sorted_contour_words:
        # ...
        cnt_chars, _ = cv2.findContours(roi_word.copy(), cv2.RETR_EXTERNAL, cv2.CHAIN_APPROX_NONE)
        sorted_contour_chars = sorted(cnt_chars, key=lambda cntr: cv2.boundingRect  (cntr)[0])
        # ...
        for character in sorted_contour_chars:
            # ...
            characters_list.append([char_x, char_y, char_x + char_w, char_y + char_h])
            cv2.rectangle(img3, (char_x, char_y), (char_x + char_w, char_y + char_h), (0, 255, 255), 2)

Pada tahap ini, dilakukan pemrosesan kontur untuk mendapatkan kotak pembatas (bounding box) untuk setiap karakter pada setiap baris dan kata dalam gambar. Kotak pembatas ini digunakan untuk memisahkan karakter-karakter tersebut. Selain itu, kotak pembatas juga digambarkan pada gambar asli dengan menggunakan fungsi cv2.rectangle.

plt.imshow(img3)  
plt.show()

Hasil segmentasi karakter ditampilkan menggunakan fungsi plt.imshow dan plt.show dari library Matplotlib.

## Link referensi

https://media.neliti.com/media/publications/323559-analisis-teknik-segmentasi-pada-pengolah-22d5da5e.pdf

https://informatika.stei.itb.ac.id/~rinaldi.munir/Citra/2019-2020/17-Segmentasi-Citra.pdf

