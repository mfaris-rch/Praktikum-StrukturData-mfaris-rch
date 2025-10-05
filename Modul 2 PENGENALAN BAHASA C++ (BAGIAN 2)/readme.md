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
> ![alt](output/array.png)
>Program tersebut bertujuan untuk menampilkan isi dari sebuah array integer. Pertama, program menginisialisasi sebuah array bernama nilai yang memiliki 5 elemen, yaitu {1, 2, 3, 4, 5}. Selanjutnya, program menggunakan perulangan for untuk mengakses setiap elemen array satu per satu, mulai dari indeks ke-0 hingga ke-4. Di dalam setiap perulangan, program akan mencetak ke layar nomor indeks beserta nilai elemen yang tersimpan pada indeks tersebut, sehingga menghasilkan output berupa daftar urutan elemen array dari awal hingga akhir. 2"

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
> ![alt](output/array2.png)
> Tentu, ini deskripsinya:

Program ini mendemonstrasikan cara menampilkan isi dari sebuah array dua dimensi atau matriks berukuran 3x3. Pertama, program mendeklarasikan dan menginisialisasi matriks integer bernama matriks dengan nilai dari 1 hingga 9. Kemudian, program menggunakan perulangan for bersarang (nested loop) untuk mengakses setiap elemen. Perulangan luar (i) akan mengiterasi setiap baris, sementara perulangan dalam (j) akan mengiterasi setiap kolom di dalam baris tersebut. Di dalam perulangan, setiap elemen matriks[i][j] dicetak ke layar, dan setelah satu baris selesai dicetak, perintah cout << endl; dieksekusi untuk pindah ke baris baru, sehingga output yang dihasilkan akan berbentuk matriks 3x3 yang rapi.

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
> ![alt](output/pointer.png)
> Program C++ ini mendemonstrasikan cara kerja pointer dengan membuat pointer p_umur yang menunjuk ke alamat memori variabel umur. Program kemudian mencetak nilai dan alamat memori variabel umur, baik secara langsung maupun melalui pointer, untuk membuktikan bahwa pointer tersebut berhasil menyimpan alamat dan dapat digunakan untuk mengakses kembali nilai aslinya.

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
> ![alt](output/arraypointer.png)
> Program ini mendemonstrasikan dua cara berbeda untuk mengakses dan menampilkan elemen-elemen dari sebuah array integer bernama data. Cara pertama adalah metode konvensional menggunakan looping dan indeks data[i]. Cara kedua adalah dengan menggunakan pointer p_data yang diarahkan ke alamat awal array, kemudian looping dan mengakses setiap elemen menggunakan notasi pointer aritmetika *(p_data + i). Kedua metode tersebut pada dasarnya melakukan hal yang sama dan akan menghasilkan output yang identik, yaitu menampilkan nilai dari setiap elemen array secara berurutan.

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
> ![alt](output/stringpointer.png)
> Program C++ ini mendemonstrasikan perbedaan mendasar antara mendeklarasikan string menggunakan char array (pesan_array) dan char pointer (pesan_pointer). Program ini menunjukkan bahwa string yang disimpan dalam char array bersifat dapat diubah, terbukti ketika karakter pertama "Nasi Padang" berhasil diubah menjadi 'h'. Sebaliknya, char pointer yang menunjuk ke sebuah string literal ("Ayam Bakar 23") merujuk pada data di memori yang sebaiknya tidak diubah, namun pointernya itu sendiri dapat diarahkan ulang untuk menunjuk ke string literal yang lain, seperti yang ditunjukkan saat pesan_pointer diubah untuk menunjuk ke "Sariman".

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
> ![alt](output/fungsiprosedur.png)
> Program C++ ini mendemonstrasikan penggunaan fungsi untuk melakukan operasi aritmetika sederhana. Program utama (main) menginisialisasi dua variabel integer, angka1 dan angka2, dengan nilai 15 dan 10. Kemudian, program memanggil fungsi hitungJumlah untuk menjumlahkan kedua angka tersebut dan menyimpan hasilnya dalam variabel hasilJumlah. Terakhir, fungsi tampilkanHasil dipanggil untuk mencetak hasil penjumlahan (yaitu 25) ke layar konsol dengan pesan yang informatif.


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
> ![alt](output/callbypointer.png)
> Program C++ ini menunjukkan cara menukar nilai dua variabel menggunakan konsep *pointer*. Fungsi `tukar` menerima dua parameter berupa alamat memori dari variabel `a` dan `b`, lalu menukar nilainya dengan bantuan variabel sementara `temp`. Di dalam fungsi `main`, nilai awal `a` dan `b` ditampilkan sebelum dan sesudah pemanggilan fungsi `tukar`, sehingga terlihat bahwa nilai `a` yang awalnya 10 menjadi 20, dan `b` yang awalnya 20 menjadi 10. Program ini merupakan contoh sederhana dari teknik *call by pointer*, yang memungkinkan perubahan nilai variabel asli melalui alamat memori.

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
> ![alt](output/callbyreference.png)
> Program C++ ini memperlihatkan cara menukar nilai dua variabel menggunakan teknik *call by reference*. Fungsi `tukar` menerima dua parameter berupa referensi (`int &x` dan `int &y`), sehingga perubahan nilai yang dilakukan di dalam fungsi langsung memengaruhi variabel asli yang dikirim dari fungsi `main`. Sebelum dan sesudah pemanggilan fungsi `tukar`, program mencetak nilai variabel `a` dan `b` ke layar, menunjukkan bahwa nilai `a` dan `b` berhasil ditukar tanpa menggunakan pointer. Pendekatan ini lebih sederhana dan aman dibandingkan penggunaan pointer, serta sangat berguna dalam pemrograman C++ modern.

## UnGuided

### Soal 1
> ![alt](soal/soal1.png)
```c++
#include <iostream>
using namespace std;

int main() {
    int matriks[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    int transpose[3][3];

    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            transpose[j][i] = matriks[i][j];
        }
    }

    cout << "Matriks Awal:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << matriks[i][j] << " ";
        }
        cout << endl;
    }

    cout << endl;

    cout << "Matriks Hasil Transpose:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            cout << transpose[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}

```
> Output
> ![alt](output/unguided1.png)
>Program C++ ini berfungsi untuk melakukan transpose terhadap sebuah matriks berukuran 3x3. Transpose adalah proses menukar baris menjadi kolom dan sebaliknya. Program mendeklarasikan matriks awal dengan nilai 1 hingga 9, lalu membuat matriks baru bernama transpose untuk menyimpan hasil transposenya. Proses penukaran dilakukan dengan perulangan bersarang, di mana elemen matriks[i][j] dipindahkan ke transpose[j][i]. Setelah itu, program mencetak matriks awal dan hasil transposenya ke layar, sehingga pengguna dapat melihat perubahan struktur data secara visual.

### Soal 2
> ![alt](soal/soal2.png)
```c++
#include <iostream>
using namespace std;

void kuadratkan(int &x) {
    x = x * x;
}

int main() {
    int angka = 5;

    cout << "Nilai awal: " << angka << endl;
    kuadratkan(angka);
    cout << "Nilai setelah dikuadratkan: " << angka << endl;

    return 0;
}
```
> Output
> ![alt](output/unguided2.png)
> Program ini menunjukkan penggunaan fungsi dengan parameter referensi untuk memodifikasi nilai variabel secara langsung. Fungsi kuadratkan menerima referensi dari variabel x, lalu mengubah nilainya menjadi hasil kuadrat dari nilai semula. Di dalam fungsi main, variabel angka diinisialisasi dengan nilai 5, kemudian dicetak sebelum dan sesudah pemanggilan fungsi kuadratkan. Karena parameter dikirim sebagai referensi, perubahan yang dilakukan dalam fungsi langsung memengaruhi nilai asli angka, sehingga hasil akhirnya adalah 25.

## Referensi

1. [https://en.wikipedia.org/wiki/Data_structure (diakses blablabla)](https://www.belajarcpp.com/tutorial/cpp/pengenalan-cpp/)
2. https://rumahcoding.co.id/pengenalan-dasar-bahasa-c-c-mulai-dari-hello-world-hingga-struktur-dasar-program/


