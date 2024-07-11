Teori geometri citra dalam pengolahan citra digital berfokus pada penggunaan konsep dan metode geometri untuk menganalisis dan 
memanipulasi citra digital. Salah satu konsep utama adalah transformasi geometris, yang melibatkan operasi untuk mengubah posisi,
orientasi, atau skala objek dalam citra. Transformasi ini meliputi translasi, rotasi, penskalaan, dan shearing. Translasi memindahkan 
objek dari satu posisi ke posisi lain tanpa mengubah bentuk atau orientasinya, sedangkan rotasi memutar objek di sekitar titik tertentu. 
Penskalaan mengubah ukuran objek, baik memperbesar maupun memperkecil, dan shearing menggeser satu bagian objek ke arah tertentu sehingga menghasilkan efek miring.
Selain transformasi dasar, konsep penting lainnya adalah pemetaan perspektif, yang digunakan untuk merepresentasikan objek tiga dimensi dalam citra dua dimensi. 
Pemetaan ini sangat penting dalam aplikasi seperti pemrosesan citra medis dan visi komputer, di mana pemahaman mendalam tentang struktur geometris objek sangat diperlukan. 
Warping dan morfing juga merupakan teknik yang digunakan untuk mengubah bentuk citra dengan cara yang lebih kompleks dan biasanya digunakan dalam grafik komputer dan animasi.
Penggunaan algoritma deteksi fitur geometri, seperti deteksi tepi dan sudut, juga esensial dalam pengolahan citra digital.
Deteksi tepi digunakan untuk menemukan batas objek dalam citra, sementara deteksi sudut membantu dalam pengenalan pola dan analisis bentuk. 
Metode seperti transformasi Hough juga digunakan untuk mendeteksi bentuk geometris seperti garis, lingkaran, dan elips dalam citra. 
Secara keseluruhan, teori geometri citra memainkan peran penting dalam berbagai aplikasi pengolahan citra, mulai dari analisis medis hingga sistem pengenalan wajah dan robotika.

Transformasi geometris pada citra adalah teknik penting dalam pemrosesan gambar yang memungkinkan manipulasi struktur spasial citra untuk berbagai tujuan, seperti rotasi, penskalaan, pemotongan, pembalikan, dan translasi.
Setiap teknik memiliki aplikasi praktis dalam berbagai bidang, termasuk pengolahan citra medis, pengenalan pola, dan visi komputer.

Rotasi adalah proses memutar citra di sekitar titik pusatnya. Ini dilakukan dengan menentukan matriks rotasi yang menggambarkan sudut rotasi dan skala, lalu menerapkannya pada citra asli. 
Misalnya, memutar citra sebesar 45 derajat mengharuskan kita menghitung matriks rotasi dan menggunakan operasi warp affine untuk menghasilkan citra yang telah diputar.
Operasi ini sering digunakan dalam aplikasi seperti koreksi orientasi dan peningkatan citra.

Penskalaan adalah perubahan ukuran citra, baik memperbesar atau memperkecil, dengan mempertahankan aspek rasio atau mengubahnya.
Ini melibatkan penentuan dimensi baru untuk citra dan menerapkan algoritma penskalaan untuk menyesuaikan piksel citra sesuai dengan dimensi baru tersebut. 
Penskalaan sering digunakan dalam persiapan data sebelum analisis lebih lanjut atau untuk menyesuaikan citra dengan tampilan tertentu.


Pemotongan adalah teknik yang digunakan untuk mengekstrak bagian tertentu dari citra, biasanya dengan menentukan koordinat batas persegi panjang yang diinginkan. 
Ini berguna untuk fokus pada area tertentu dari citra yang mengandung informasi penting atau untuk menghilangkan area yang tidak diinginkan. 
Pemotongan sering diterapkan dalam deteksi objek dan segmentasi citra.

Pembalikan adalah proses membalik citra, baik secara horizontal maupun vertikal. Pembalikan horizontal, misalnya, mengubah sisi kiri dan kanan citra, sementara pembalikan vertikal mengubah sisi atas dan bawah. 
Teknik ini dapat digunakan dalam augmentasi data untuk meningkatkan variabilitas dataset pelatihan dalam pembelajaran mesin dan pengenalan pola.

Translasi melibatkan pergeseran citra ke posisi baru dalam bidang koordinat tanpa mengubah orientasi atau skala. Matriks translasi menentukan seberapa jauh dan ke arah mana citra harus digeser. 
Operasi ini penting dalam koreksi posisi dan registrasi citra, di mana beberapa citra dari adegan yang sama perlu diselaraskan dengan tepat.
Setiap transformasi ini diterapkan menggunakan operasi warp affine, yang mengubah koordinat piksel citra berdasarkan matriks transformasi yang sesuai. 
Kombinasi dari berbagai transformasi ini memungkinkan manipulasi kompleks citra yang dapat meningkatkan analisis dan interpretasi data citra dalam berbagai aplikasi.


Penjelasan coodingan :
-import cv2: Mengimpor OpenCV, pustaka yang digunakan untuk pemrosesan citra dan video.

-import matplotlib.pyplot as plt: Mengimpor modul pyplot dari matplotlib untuk menampilkan gambar.

-import numpy as np: Mengimpor NumPy, pustaka untuk operasi numerik yang efisien.

-image = cv2.imread('jeje.jpg'): Membaca gambar dengan nama file 'jeje.jpg' dan menyimpannya dalam variabel image.

-def display_images(images, titles): Mendefinisikan fungsi untuk menampilkan beberapa gambar dengan judul.

-plt.figure(figsize=(15, 10)): Membuat figur baru dengan ukuran 15x10 inci.

-for i in range(len(images)): Loop untuk mengiterasi melalui daftar gambar.

-plt.subplot(2, 3, i+1): Membuat subplot (2 baris dan 3 kolom).

-plt.imshow(cv2.cvtColor(images[i], cv2.COLOR_BGR2RGB)): Menampilkan gambar setelah mengonversi dari BGR (format OpenCV) ke RGB (format Matplotlib).

-plt.title(titles[i]): Menambahkan judul pada setiap gambar.

-plt.axis('off'): Menghilangkan sumbu.

-plt.show(): Menampilkan semua gambar.

-original = image.copy(): Membuat salinan gambar asli dan menyimpannya dalam variabel original.

-(h, w) = image.shape[:2]: Mendapatkan tinggi (h) dan lebar (w) gambar.

-center = (w // 2, h // 2): Menentukan titik pusat gambar.

-M = cv2.getRotationMatrix2D(center, 45, 1.0): Membuat matriks rotasi untuk memutar gambar 45 derajat.

-rotated = cv2.warpAffine(image, M, (w, h)): Menerapkan rotasi pada gambar menggunakan matriks rotasi M.

-new_height = int(h * 1.5): Menentukan tinggi baru dengan meningkatkan tinggi asli sebesar 50%.

-new_width = w: Menjaga lebar tetap sama.

-resized = cv2.resize(image, (new_width, new_height)): Mengubah ukuran gambar sesuai dimensi baru.

-cropped = image[50:200, 50:200]: Memotong gambar dari koordinat (50, 50) ke (200, 200).

-flipped = cv2.flip(image, 1): Membalik gambar secara horizontal

-M = np.float32([[1, 0, 50], [0, 1, 100]]): Membuat matriks transformasi untuk menerjemahkan gambar 50 piksel ke kanan dan 100 piksel ke bawah.

-translated = cv2.warpAffine(image, M, (w, h)): Menerapkan terjemahan pada gambar menggunakan matriks M.

-images = [original, rotated, resized, cropped, flipped, translated]: Membuat daftar semua gambar yang akan ditampilkan.

-titles = ['Citra Asli', 'After Rotated', 'After Resized', 'After Cropped', 'After Flipped', 'After Translated']: Membuat daftar judul untuk setiap gambar.

-display_images(images, titles): Memanggil fungsi display_images untuk menampilkan semua gambar dengan judul masing-masing.

