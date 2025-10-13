# <h1 align="center">Laporan Praktikum Modul 1 <br> CODE BLOCKS IDE & PENGENALAN BAHASA C++
<p align="center">Muhammad Faris Rachmadi - 103112400079</p>

## Dasar Teori

C++ adalah peluasan dan penyempurnaan dari bahasa pemrograman sebelumnya yaitu bahasa C, oleh Bjarne Stroustrup pada tahun 1980. Awal C++ mempunyai nama yaitu “C with Classes” dan berganti nama menjadi C++ pada tahun 1983. Bjarne Stroustrup membuat bahasa pemrograman C++ dengan tambahan fasilitas, yang sangat berguna pada tahun itu sampai sekarang, yaitu bahasa pemrograman yang mendukung OOP (Object Oriented Programming).

C++ dirancang sebagai bias terhadap sistem pemrograman dan embedded sistem, dengan mengutamakan kinerja, kecepatan, efisiensi dan fleksibilitas penggunaan. C++ telah dan sangat berguna dalam banyak hal, seperti pembuatan aplikasi desktop, server dan performance-critical (misalnya switch telepon dan pesawat luar angkasa).
## Guided

### Guided 1
```c++
#include <iostream>
using namespace std;

// Struktur Node
struct Node {
    int data;
    Node* next;
};

// Pointer awal dan akhir
Node* head = nullptr;

// Fungsi untuk membuat node baru
Node* createNode(int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->next = nullptr;
    return newNode;
}

void insertDepan(int data) {
    Node* newNode = createNode(data);
    newNode->next = head;
    head = newNode;
    cout << "Data " << data << " berhasil ditambahkan di depan.\n";
}

void insertBelakang(int data) {
    Node* newNode = createNode(data);
    if (head == nullptr) {
        head = newNode;
    } else {
        Node* temp = head;
        while (temp->next != nullptr) {
            temp = temp->next;
        }
        temp->next = newNode;
    }
    cout << "Data " << data << " berhasil ditambahkan di belakang.\n";
}

void insertSetelah(int target, int dataBaru) {
    Node* temp = head;
    while (temp != nullptr && temp->data != target) {
        temp = temp->next;
    }

    if (temp == nullptr) {
        cout << "Data " << target << " tidak ditemukan!\n";
    } else {
        Node* newNode = createNode(dataBaru);
        newNode->next = temp->next;
        temp->next = newNode;
        cout << "Data " << dataBaru << " berhasil disisipkan setelah " << target << ".\n";
    }
}

// ========== DELETE FUNCTION ==========
void hapusNode(int data) {
    if (head == nullptr) {
        cout << "List kosong!\n";
        return;
    }

    Node* temp = head;
    Node* prev = nullptr;

    // Jika data di node pertama
    if (temp != nullptr && temp->data == data) {
        head = temp->next;
        delete temp;
        cout << "Data " << data << " berhasil dihapus.\n";
        return;
    }

    // Cari node yang akan dihapus
    while (temp != nullptr && temp->data != data) {
        prev = temp;
        temp = temp->next;
    }

    // Jika data tidak ditemukan
    if (temp == nullptr) {
        cout << "Data " << data << " tidak ditemukan!\n";
        return;
    }

    prev->next = temp->next;
    delete temp;
    cout << "Data " << data << " berhasil dihapus.\n";
}

// ========== UPDATE FUNCTION ==========
void updateNode(int dataLama, int dataBaru) {
    Node* temp = head;
    while (temp != nullptr && temp->data != dataLama) {
        temp = temp->next;
    }

    if (temp == nullptr) {
        cout << "Data " << dataLama << " tidak ditemukan!\n";
    } else {
        temp->data = dataBaru;
        cout << "Data " << dataLama << " berhasil diupdate menjadi " << dataBaru << ".\n";
    }
}

// ========== DISPLAY FUNCTION ==========
void tampilkanList() {
    if (head == nullptr) {
        cout << "List kosong!\n";
        return;
    }

    Node* temp = head;
    cout << "Isi Linked List: ";
    while (temp != nullptr) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "NULL\n";
}

// ========== MAIN PROGRAM ==========
int main() {
    int pilihan, data, target, dataBaru;

    do {
        cout << "\n=== MENU SINGLE LINKED LIST ===\n";
        cout << "1. Insert Depan\n";
        cout << "2. Insert Belakang\n";
        cout << "3. Insert Setelah\n";
        cout << "4. Hapus Data\n";
        cout << "5. Update Data\n";
        cout << "6. Tampilkan List\n";
        cout << "0. Keluar\n";
        cout << "Pilih: ";
        cin >> pilihan;

        switch (pilihan) {
            case 1:
                cout << "Masukkan data: ";
                cin >> data;
                insertDepan(data);
                break;
            case 2:
                cout << "Masukkan data: ";
                cin >> data;
                insertBelakang(data);
                break;
            case 3:
                cout << "Masukkan data target: ";
                cin >> target;
                cout << "Masukkan data baru: ";
                cin >> dataBaru;
                insertSetelah(target, dataBaru);
                break;
            case 4:
                cout << "Masukkan data yang ingin dihapus: ";
                cin >> data;
                hapusNode(data);
                break;
            case 5:
                cout << "Masukkan data lama: ";
                cin >> data;
                cout << "Masukkan data baru: ";
                cin >> dataBaru;
                updateNode(data, dataBaru);
                break;
            case 6:
                tampilkanList();
                break;
            case 0:
                cout << "Program selesai.\n";
                break;
            default:
                cout << "Pilihan tidak valid!\n";
        }
    } while (pilihan != 0);

    return 0;
}
```
> Output
> ![alt](output/aritmatika.png)
> Program C++ ini adalah implementasi dari struktur data single linked list yang menyediakan serangkaian operasi dasar untuk memanipulasi daftar elemen secara dinamis. Program ini memungkinkan pengguna untuk melakukan berbagai macam fungsi melalui antarmuka menu sederhana, termasuk menyisipkan data baru di bagian depan, di bagian belakang, atau setelah elemen tertentu yang sudah ada di dalam list. Selain itu, program ini juga dilengkapi dengan fungsionalitas untuk menghapus elemen berdasarkan nilainya, memperbarui data pada elemen yang ada, serta menampilkan keseluruhan isi dari linked list untuk memverifikasi hasil dari setiap operasi yang dilakukan.

## UnGuided

### Soal 1
> buatlah single linked list untuk Antrian yang menyimpan data pembeli( nama dan pesanan). program memiliki beberapa menu seperti tambah antrian,  layani antrian(hapus), dan tampilkan antrian. *antrian pertama harus yang pertama dilayani
```c++
#include <iostream>
#include <string>

using namespace std;

// Struktur untuk Node Pembeli
struct Node {
    string nama;
    string pesanan;
    Node* next;
};

// Kelas untuk mengelola daftar antrian
class DaftarAntrian {
private:
    Node* depan;
    Node* belakang;

public:
    // Constructor
    DaftarAntrian() {
        depan = nullptr;
        belakang = nullptr;
    }

    bool isEmpty() {
        return depan == nullptr;
    }

    void tambah(string nama, string pesanan) {
        Node* newNode = new Node();
        newNode->nama = nama;
        newNode->pesanan = pesanan;
        newNode->next = nullptr;

        if (isEmpty()) {
            depan = belakang = newNode;
        } else {
            belakang->next = newNode;
            belakang = newNode;
        }
        cout << "\n>> " << nama << " berhasil ditambahkan." << endl;
    }

    void layani() {
        if (isEmpty()) {
            cout << "\n>> Antrian kosong." << endl;
            return;
        }

        Node* temp = depan;
        depan = depan->next;

        if (depan == nullptr) {
            belakang = nullptr;
        }
        
        cout << "\n>> Melayani: " << temp->nama << " (" << temp->pesanan << ")." << endl;
        delete temp;
    }

    void tampilkan() {
        cout << "\n===== Daftar Antrian =====" << endl;
        if (isEmpty()) {
            cout << "      Antrian kosong." << endl;
        } else {
            Node* current = depan;
            int i = 1;
            while (current != nullptr) {
                cout << i << ". " << current->nama << " - Pesanan: " << current->pesanan << endl;
                current = current->next;
                i++;
            }
        }
        cout << "==========================" << endl;
    }
};

// Fungsi utama
int main() {
    DaftarAntrian antrian; // Menggunakan kelas DaftarAntrian
    int pilihan;
    string nama, pesanan;

    do {
        cout << "\n\n=== MENU ANTRIAN ===";
        cout << "\n1. Tambah Antrian";
        cout << "\n2. Layani Antrian";
        cout << "\n3. Tampilkan Antrian";
        cout << "\n4. Keluar";
        cout << "\n\nPilih menu: ";
        cin >> pilihan;
        cin.ignore(); 

        switch (pilihan) {
            case 1:
                cout << "Masukkan Nama: ";
                getline(cin, nama);
                cout << "Masukkan Pesanan: ";
                getline(cin, pesanan);
                antrian.tambah(nama, pesanan);
                break;
            case 2:
                antrian.layani();
                break;
            case 3:
                antrian.tampilkan();
                break;
            case 4:
                cout << "\nProgram selesai." << endl;
                break;
            default:
                cout << "\n>> Pilihan tidak valid." << endl;
                break;
        }
    } while (pilihan != 4);

    return 0;
}
```
> Output
> ![alt](output/soal1.png)
> Program ini merupakan implementasi sistem antrian sederhana menggunakan struktur data single linked list dalam bahasa C++. Sistem ini dirancang untuk mengelola data pembeli yang terdiri dari nama dan pesanan, dengan menerapkan prinsip FIFO (First-In, First-Out), di mana pembeli yang pertama datang akan dilayani terlebih dahulu. Pengguna dapat berinteraksi melalui menu konsol untuk melakukan tiga operasi utama: menambah pembeli baru ke akhir antrian, melayani (menghapus) pembeli dari awal antrian, dan menampilkan seluruh daftar antrian yang ada saat ini.

### Soal 2
> buatlah program kode untuk membalik (reverse) singly linked list (1-2-3 menjadi 3-2-1)
```c++
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void append(Node** head_ref, int new_data) {
    Node* new_node = new Node();
    new_node->data = new_data;
    new_node->next = nullptr;

    if (*head_ref == nullptr) {
        *head_ref = new_node;
        return;
    }

    Node* last = *head_ref;
    while (last->next != nullptr) {
        last = last->next;
    }
    last->next = new_node;
}

void reverse(Node** head_ref) {
    Node* prev = nullptr;
    Node* current = *head_ref;
    Node* next = nullptr;

    while (current != nullptr) {
        next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    *head_ref = prev;
}

void printList(Node* node) {
    while (node != nullptr) {
        cout << node->data << " -> ";
        node = node->next;
    }
    cout << "NULL" << endl;
}

int main() {
    Node* head = nullptr;

    append(&head, 1);
    append(&head, 2);
    append(&head, 3);

    cout << "List Awal  : ";
    printList(head);

    reverse(&head);

    cout << "List Dibalik: ";
    printList(head);

    return 0;
}
```
> Output
> ![alt](output/soal2.png)
> Program C++ ini mendemonstrasikan operasi dasar pada *singly linked list* dengan membuat sebuah list sederhana berisi data `1 -> 2 -> 3`. Fungsi utamanya adalah `reverse`, yang secara iteratif membalik urutan node dalam list tersebut menggunakan tiga pointer (prev, current, next) untuk mengubah arah pointer `next` dari setiap node. Akhirnya, program ini mencetak kondisi list sebelum dan sesudah dibalik untuk menunjukkan bahwa urutannya telah berhasil diubah dari `1 -> 2 -> 3` menjadi `3 -> 2 -> 1`.

## Referensi

1. [https://en.wikipedia.org/wiki/Data_structure (diakses blablabla)](https://www.belajarcpp.com/tutorial/cpp/pengenalan-cpp/)
2. https://rumahcoding.co.id/pengenalan-dasar-bahasa-c-c-mulai-dari-hello-world-hingga-struktur-dasar-program/


