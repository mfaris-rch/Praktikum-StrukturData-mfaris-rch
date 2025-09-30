# <h1 align="center">Laporan Praktikum Modul 2 <br> PENGENALAN BAHASA C++ (BAGIAN 2)
<p align="center">Muhammad Faris Rachmadi - 103112400079</p>

## Dasar Teori

C++ adalah peluasan dan penyempurnaan dari bahasa pemrograman sebelumnya yaitu bahasa C, oleh Bjarne Stroustrup pada tahun 1980. Awal C++ mempunyai nama yaitu “C with Classes” dan berganti nama menjadi C++ pada tahun 1983. Bjarne Stroustrup membuat bahasa pemrograman C++ dengan tambahan fasilitas, yang sangat berguna pada tahun itu sampai sekarang, yaitu bahasa pemrograman yang mendukung OOP (Object Oriented Programming).

C++ dirancang sebagai bias terhadap sistem pemrograman dan embedded sistem, dengan mengutamakan kinerja, kecepatan, efisiensi dan fleksibilitas penggunaan. C++ telah dan sangat berguna dalam banyak hal, seperti pembuatan aplikasi desktop, server dan performance-critical (misalnya switch telepon dan pesawat luar angkasa).
## Guided

### 01_array
```c++
#include <iostream>
using namespace std;

int main(){
    int nilai[5] = {1, 2, 3, 4, 5};
    for (int i = 0; i < 5; ++i)
    {
        cout << "Elemen ke-" << i << " = " << nilai[i] << endl;
    }
    return 0;
}
```
> Output
> ![alt](output/aritmatika.png)
> Program di atas merupakan program sederhana dalam bahasa C++ yang melakukan operasi aritmatika menggunakan variabel bertipe integer dan float. Variabel X, Y, dan W didefinisikan sebagai integer, lalu diberi nilai masing-masing X = 7, Y = 3, dan W = 1. Kemudian variabel Z bertipe float digunakan untuk menyimpan hasil perhitungan (X + Y) / (Y + W). Karena X + Y = 10 dan Y + W = 4, maka hasil pembagian adalah 10 / 4 = 2 (hasilnya integer karena operasi dilakukan antar bilangan bulat), lalu disimpan ke dalam variabel float Z, sehingga Z bernilai 2.0. Program kemudian menampilkan hasil tersebut di layar dengan perintah cout, sehingga output yang muncul adalah "Nilai z = 2"

### 02_array
```c++
#include <iostream>
using namespace std;

int main()

{
    int matriks[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}};

    for (int i = 0; i < 3; ++i)
    {
        for (int j = 0; j < 3; ++j)
        {
            cout << matriks[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```
> Output
> ![alt](output/fungsi.png)
> Program C++ di atas digunakan untuk menghitung luas dan keliling persegi panjang dengan memanfaatkan fungsi dan prosedur. Fungsi hitungLuas dan hitungKeliling digunakan untuk mengembalikan nilai hasil perhitungan, sedangkan prosedur tampilkanHasil hanya menampilkan data tanpa mengembalikan nilai. Pada bagian main, pengguna diminta memasukkan panjang dan lebar, kemudian program menghitung luas serta keliling dengan fungsi, lalu menampilkan hasilnya kembali melalui prosedur.
### 03_pointer
```c++
#include <iostream>
using namespace std;

int main()
{
    int umur = 25;
    int *p_umur;

    p_umur = &umur;

    cout << "Nilai 'umur': " << umur << endl;
    cout << "Alamat memeori 'umur': " << &umur << endl;
    cout << "Nilai 'p_umur' (alamat): " <<p_umur << endl;
    cout << "Nilai yang diakses 'p_umur': " << *p_umur << endl;
    cout << "Alamat memori dari pointer 'p_umur' itu sendiri: " << &p_umur << endl;

    return 0;
}
```
> Output
> ![alt](output/kondisi.png)
> Program C++ di atas terdiri dari beberapa contoh kode, namun yang aktif adalah bagian terakhir yang digunakan untuk menentukan apakah suatu hari termasuk hari kerja atau hari libur. Pengguna diminta memasukkan kode angka (1–7) yang mewakili hari dalam seminggu. Jika angka yang dimasukkan adalah 1 sampai 5 (Senin–Jumat), maka program menampilkan "Hari Kerja". Jika angka 6 atau 7 (Sabtu–Minggu), program menampilkan "Hari Libur". Apabila input tidak sesuai dengan 1–7, program akan menampilkan pesan "Kode masukan salah!!!".
### 04_array_pointer
```c++
#include <iostream>
using namespace std;

int main()
{
    int data[5] = {10, 20, 30, 40, 50};
    int *p_data = data;

    cout << "Mengakses elemen array cara normal: " << endl;

    for (int i = 0; i < 5; ++i)
    {
        cout << "Nilai elemen ke- " << i << ": " << data[i] << endl;
    }

    cout << "Mengakses elemen array menggunakan pointer:" << endl;

    for (int i = 0; i < 5; ++i)
    {
        cout << "Nilai elemen ke-" << i << ": " << *(p_data + i) << endl;
    }
    return 0;
}
```
> Output
> ![alt](output/perulangan.png)
> Program C++ di atas menunjukkan penggunaan **perulangan (looping)**. Pada bagian yang dikomentari digunakan **for loop** untuk menampilkan teks sebanyak jumlah yang dimasukkan. Sedangkan bagian aktif menggunakan **do-while loop**, di mana program meminta input jumlah perulangan, lalu mencetak tulisan **"bahlil ke-"** disertai nomor urut mulai dari 2, dan terus berulang selama nilai `i` masih lebih kecil dari jumlah yang dimasukkan. Dengan demikian, output akan menampilkan teks berulang sesuai jumlah perulangan yang diinputkan pengguna.

### 05_string_pointer
```c++
#include <iostream>
using namespace std;

int main()
{
    char pesan_array[] = "Nasi Padang";
    char* pesan_pointer = "Ayam Bakar 23";

    cout << "String Array: " << pesan_array << endl;
    cout << "String Pointer: " << pesan_pointer << endl;

    // Mengubah karakter dalam array diperbolehkan
    pesan_array[0] = 'h';
    cout << "String Array setelah diubah: " << pesan_array << endl;

    // Pointer dapat diubah untuk menunjuk ke string lain
    pesan_pointer = "Sariman";
    cout << "String Pointer setelah menunjuk ke string lain: " << pesan_pointer << endl;

    return 0;
}
```
> Output
> ![alt](output/struct.png)
> Program C++ di atas menggunakan struct untuk menyimpan data mahasiswa. Struct bernama Mahasiswa memiliki tiga atribut, yaitu nama, nim, dan ipk. Pada fungsi main, dibuat sebuah variabel mhs1 dari tipe Mahasiswa. Program meminta pengguna memasukkan nama, NIM, dan IPK, lalu menyimpannya ke dalam variabel tersebut. Setelah itu, program menampilkan kembali data mahasiswa yang sudah dimasukkan ke layar dengan format yang rapi.

### 06_fungsi_prosedur
```c++
#include <iostream>

int hitungJumlah(int a, int b)
{
    return a + b;
}

void tampilkanHasil(int hasil)
{
    std::cout << "Hasil penjumlahannya adalah: " << hasil << std::endl;
}

int main()
{
    int angka1 = 15;
    int angka2 = 10;
    int hasilJumlah;

    hasilJumlah = hitungJumlah(angka1, angka2);
    tampilkanHasil(hasilJumlah);

    return 0;
}
```
> Output
> ![alt](output/test.png)
> Program C++ di atas digunakan untuk **membaca satu karakter input dari pengguna**. Variabel `ch` dideklarasikan sebagai `string`, lalu program meminta pengguna memasukkan sebuah karakter. Input dibaca dengan fungsi `getchar()`, yang mengambil satu karakter dari keyboard. Karakter yang dimasukkan kemudian ditampilkan kembali melalui `cout`. Jadi, program ini sederhana untuk menampilkan kembali karakter tunggal yang diketikkan oleh pengguna.


### 07_call_by_pointer
```c++
#include <iostream>
using namespace std;

void tukar(int *px, int *py)
{
    int temp = *px;
    *px = *py;
    *py = temp;
}

int main()
{
    int a = 10, b = 20;
    cout << "Sebelum ditukar: a = " << a << ", b = " << b << endl;
    tukar(&a, &b);
    cout << "Setelah ditukar: a = " << a << ", b = " << b << endl;
    return 0;
}
```
> Output
> ![alt](output/test.png)
> Program C++ di atas digunakan untuk **membaca satu karakter input dari pengguna**. Variabel `ch` dideklarasikan sebagai `string`, lalu program meminta pengguna memasukkan sebuah karakter. Input dibaca dengan fungsi `getchar()`, yang mengambil satu karakter dari keyboard. Karakter yang dimasukkan kemudian ditampilkan kembali melalui `cout`. Jadi, program ini sederhana untuk menampilkan kembali karakter tunggal yang diketikkan oleh pengguna.

### 08_call_by_reference
```c++
#include <iostream>
using namespace std;

void tukar(int &x, int &y)
{
    int temp = x;
    x = y;
    y = temp;
}

int main()
{
    int a = 10, b = 20;
    cout << "Sebelum ditukar: a = " << a << ", b = " << b << endl;
    tukar(a, b);
    cout << "Setelah ditukar: a = " << a << ", b = " << b << endl;
    return 0;
}
```
> Output
> ![alt](output/test.png)
> Program C++ di atas digunakan untuk **membaca satu karakter input dari pengguna**. Variabel `ch` dideklarasikan sebagai `string`, lalu program meminta pengguna memasukkan sebuah karakter. Input dibaca dengan fungsi `getchar()`, yang mengambil satu karakter dari keyboard. Karakter yang dimasukkan kemudian ditampilkan kembali melalui `cout`. Jadi, program ini sederhana untuk menampilkan kembali karakter tunggal yang diketikkan oleh pengguna.

## UnGuided

### Soal 1
> ![alt](soal/S1.png)
```c++
#include <iostream>
using namespace std;

int main(){
    float x, y;

    cout << "Masukkan Bilangan Pertama: ";
    cin >> x;
    cout << "Masukkan Bilangan Kedua: ";
    cin >> y;

       cout << "\nHasil Operasi:\n";
    cout << "Penjumlahan      = " << x + y << endl;
    cout << "Pengurangan      = " << x - y << endl;
    cout << "Perkalian        = " << x * y << endl;
    cout << "Pembagian        = " << x / y << endl;

    return 0;
}
```
> Output
> ![alt](output/soal1.png)
> Program C++ di atas adalah program sederhana untuk melakukan **empat operasi aritmatika dasar**. Program meminta pengguna memasukkan dua bilangan bertipe `float`, kemudian menghitung hasil **penjumlahan, pengurangan, perkalian, dan pembagian** dari kedua bilangan tersebut. Setelah perhitungan, hasil masing-masing operasi ditampilkan ke layar dengan format yang jelas. Program ini berguna sebagai contoh dasar penggunaan input (`cin`), output (`cout`), serta operasi aritmatika dalam C++.

### Soal 2
> ![alt](soal/S2.png)
```c++
#include <iostream>
using namespace std;

int main() {
    string satuan[] = {"", "satu", "dua", "tiga", "empat", "lima", 
                       "enam", "tujuh", "delapan", "sembilan"};
    string puluhan[] = {"", "sepuluh", "dua puluh", "tiga puluh", "empat puluh", 
                        "lima puluh", "enam puluh", "tujuh puluh", 
                        "delapan puluh", "sembilan puluh"};
    

    int bil;
    cout << "Masukkan angka (0-100): ";
    cin >> bil;

    if (bil == 0) cout << "nol";
    else if (bil == 10) cout << "sepuluh";
    else if (bil == 11) cout << "sebelas";
    else if (bil < 20) cout << satuan[bil - 10] << " belas";      
    else if (bil < 100) {
        cout << puluhan[bil / 10];
        if (bil % 10 != 0) cout << " " << satuan[bil % 10];       
    }
    else if (bil == 100) cout << "seratus";

    return 0;
}
```
> Output
> ![alt](output/soal2.png)
> Program C++ di atas digunakan untuk **mengonversi angka menjadi teks dalam bahasa Indonesia** pada rentang 0 sampai 100. Program memanfaatkan dua array string, yaitu `satuan` untuk angka 1–9 dan `puluhan` untuk kelipatan 10. Setelah pengguna memasukkan angka, program akan mengecek kondisinya dengan `if-else`: angka 0 ditampilkan sebagai "nol", angka 10 "sepuluh", angka 11 "sebelas", angka 12–19 ditulis dalam bentuk "… belas", angka 20–99 ditulis dengan format "… puluh …", dan angka 100 ditampilkan sebagai "seratus". Dengan logika tersebut, misalnya jika input adalah 79, output yang muncul adalah "tujuh puluh sembilan".

### Soal 3
> ![alt](soal/S3.png)
```c++
#include <iostream>
using namespace std;

int main() {
    int a;
    cout << "Input: ";
    cin >> a;

    cout << "Output:" << endl;
    for (int i = a; i >= 1; i--) {
        for (int s = 0; s < (a - i); s++) {
            cout << "  "; 
        }
        // kiri (turun)
        for (int j = i; j >= 1; j--) {
            cout << j << " ";
        }
        cout << "* "; 
        for (int j = 1; j <= i; j++) {
            cout << j << " ";
        }
        cout << endl;
    }

    for (int s = 0; s < a; s++) {
        cout << "  "; // spasi ganda
    }
    cout << "*" << endl;

    return 0;
}
```
> Output
> ![alt](output/soal3.png)
> Program C++ di atas menampilkan pola simetris angka dengan tanda bintang (*) di tengah. Input bilangan a menentukan tinggi pola, lalu dengan perulangan for dibuat deretan angka menurun di kiri, bintang di tengah, dan angka menaik di kanan, disertai spasi agar rata. Terakhir ditampilkan satu bintang di bagian bawah tengah.


## Referensi

1. [https://en.wikipedia.org/wiki/Data_structure (diakses blablabla)](https://www.belajarcpp.com/tutorial/cpp/pengenalan-cpp/)
2. https://rumahcoding.co.id/pengenalan-dasar-bahasa-c-c-mulai-dari-hello-world-hingga-struktur-dasar-program/


