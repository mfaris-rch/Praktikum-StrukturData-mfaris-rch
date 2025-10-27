# <h1 align="center">Laporan Praktikum Modul 6 <br> DOUBLY LINKED LIST (BAGIAN KEDUA)
<p align="center">Muhammad Faris Rachmadi - 103112400079</p>

## Dasar Teori
Doubly Linked List adalah salah satu bentuk struktur data dinamis yang terdiri dari rangkaian elemen (node), di mana setiap node memiliki dua pointer, yaitu next yang menunjuk ke elemen berikutnya dan prev yang menunjuk ke elemen sebelumnya. Berbeda dengan Singly Linked List yang hanya dapat diakses satu arah, Doubly Linked List memungkinkan proses penelusuran data secara dua arah, baik maju maupun mundur. Struktur ini memiliki dua pointer utama yaitu first yang menunjuk ke elemen pertama dan last yang menunjuk ke elemen terakhir dalam list. Keunggulan Doubly Linked List terletak pada kemudahannya dalam melakukan operasi penyisipan dan penghapusan data di berbagai posisi karena dapat mengakses node secara fleksibel dari kedua arah, meskipun membutuhkan memori lebih besar untuk menyimpan dua pointer di setiap elemen. Doubly Linked List banyak digunakan dalam implementasi program yang memerlukan navigasi data dua arah seperti daftar riwayat, sistem navigasi, dan manajemen memori dinamis.
## Guided

### Guided 1
```c++
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* prev;
    Node* next;
};

Node* head = nullptr;
Node* tail = nullptr;

void insertDepan(int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->prev = nullptr;
    newNode->next = head;

    if (head != nullptr)
        head->prev = newNode;
    else
        tail = newNode;

    head = newNode;
    cout << "Data " << data << " berhasil ditambahkan di depan.\n";
}

void insertBelakang(int data) {
    Node* newNode = new Node();
    newNode->data = data;
    newNode->next = nullptr;
    newNode->prev = tail;

    if (tail != nullptr)
        tail->next = newNode;
    else
        head = newNode;

    tail = newNode;
    cout << "Data " << data << " berhasil ditambahkan di belakang.\n";
}

void insertSetelah(int target, int data) {
    Node* current = head;
    while (current != nullptr && current->data != target)
        current = current->next;
    
    if (current == nullptr) {
        cout << "Data " << target << " tidak ditemukan.\n";
        return;
    }

    Node* newNode = new Node();
    newNode->data = data;
    newNode->next = current->next;
    newNode->prev = current;

    if (current->next != nullptr)
        current->next->prev = newNode;
    else
        tail = newNode;

    current->next = newNode;
    cout << "Data " << data << " berhasil disisipkan setelah " << target << ".\n";
}

void hapusDepan() {
    if (head == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    Node* temp = head;
    head = head->next;

    if (head != nullptr)
        head->prev = nullptr;
    else
        tail = nullptr;

    cout << "Data " << temp->data << " dihapus dari depan.\n";
    delete temp;
}

void hapusBelakang() {
    if (tail = nullptr) {
        cout << "List kosong.\n";
        return;
    }

    Node* temp = tail;
    tail = tail->prev;

    if (tail != nullptr)
        tail->next = nullptr;
    else
        head = nullptr;

    cout << "Data " << temp->data << " dihapus dari belakang.\n";
    delete temp;
}

void hapusData(int target) {
    if (head == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    Node* current = head;
    while (current != nullptr && current->data != target)
        current = current->next;

    if (current == head)
        hapusDepan();
    else if (current == tail)
        hapusBelakang();
    else {
        current->prev->next = current->next;
        current->next->prev = current->prev;
        cout << "Data " << target << " dihapus.\n";
        delete current;
    }
}

void updateData(int oldData, int newData) {
    Node* current = head;
    while (current != nullptr && current->data != oldData)
        current = current->next;

    if (current == nullptr) {
        cout << "Data " << oldData << " tidak ditemukan.\n";
        return;
    }

    current->data = newData;
    cout << "Data " << oldData << " diubah menjadi " << newData << ".\n";
}

void tampilDepan() {
    if (head == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    cout << "Isi list (dari depan): ";
    Node* current = head;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->next;
    }
    cout << "\n";
}

// ====================================
// Fungsi: Tampilkan dari belakang
// ====================================
void tampilBelakang() {
    if (tail == nullptr) {
        cout << "List kosong.\n";
        return;
    }

    cout << "Isi list (dari belakang): ";
    Node* current = tail;
    while (current != nullptr) {
        cout << current->data << " ";
        current = current->prev;
    }
    cout << "\n";
}

// ====================================
// MAIN PROGRAM (MENU INTERAKTIF)
// ====================================
int main() {
    int pilihan, data, target, oldData, newData;

    do {
        cout << "\n===== MENU DOUBLE LINKED LIST =====\n";
        cout << "1. Insert Depan\n";
        cout << "2. Insert Belakang\n";
        cout << "3. Insert Setelah Data\n";
        cout << "4. Hapus Depan\n";
        cout << "5. Hapus Belakang\n";
        cout << "6. Hapus Data Tertentu\n";
        cout << "7. Update Data\n";
        cout << "8. Tampil dari Depan\n";
        cout << "9. Tampil dari Belakang\n";
        cout << "0. Keluar\n";
        cout << "===================================\n";
        cout << "Pilih menu: ";
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
                cin >> data;
                insertSetelah(target, data);
                break;
            case 4:
                hapusDepan();
                break;
            case 5:
                hapusBelakang();
                break;
            case 6:
                cout << "Masukkan data yang ingin dihapus: ";
                cin >> target;
                hapusData(target);
                break;
            case 7:
                cout << "Masukkan data lama: ";
                cin >> oldData;
                cout << "Masukkan data baru: ";
                cin >> newData;
                updateData(oldData, newData);
                break;
            case 8:
                tampilDepan();
                break;
            case 9:
                tampilBelakang();
                break;
            case 0:
                cout << "👋 Keluar dari program.\n";
                break;
            default:
                cout << "Pilihan tidak valid.\n";
        }

    } while (pilihan != 0);

    return 0;
}
```
> Output
> ![alt](output/guided.png)
> Program di atas merupakan implementasi struktur data Doubly Linked List dalam bahasa C++ yang menyediakan berbagai operasi manipulasi data menggunakan menu interaktif. Setiap elemen disimpan dalam node yang memiliki pointer ke node sebelumnya (prev) dan node berikutnya (next), sehingga memungkinkan penelusuran dua arah. Program ini memiliki fungsi untuk menambahkan data di depan (insertDepan), di belakang (insertBelakang), atau setelah data tertentu (insertSetelah), serta menghapus data dari depan (hapusDepan), belakang (hapusBelakang), atau berdasarkan nilai tertentu (hapusData). Selain itu, terdapat fitur untuk memperbarui isi data (updateData) dan menampilkan isi list dari arah depan (tampilDepan) maupun belakang (tampilBelakang). Dengan menu yang interaktif, pengguna dapat dengan mudah melakukan operasi CRUD (Create, Read, Update, Delete) pada struktur data Doubly Linked List secara dinamis.

## UnGuided

### doublylist.h
```c++
#ifndef DOUBLYLIST_H
#define DOUBLYLIST_H

#include <iostream>
#include <string>

using namespace std;

struct Infotype {
    string nopol;
    string warna;
    int thnbuat;
};

typedef struct Elmlist *address;

struct Elmlist {
    Infotype info;
    address next;
    address prev;
};

struct List {
    address First;
    address Last;
};

#define First(L) (L).First
#define Last(L) (L).Last
#define Info(P) (P)->info
#define Next(P) (P)->next
#define Prev(P) (P)->prev

void CreateList(List &L);
address alokasi(Infotype X);
void dealokasi(address &P);
void insertlast(List &L, address P);
void printinfo(List L);

address findElm(List L, string nopol);

void deleteFirst(List &L, address &P);
void deleteLast(List &L, address &P);
void deleteAfter(address Prec, address &P);

void deleteByNopol(List &L, string nopol);

#endif
```

### doublylist.cpp
```c++
#include "doublylist.h"

void CreateList(List &L) {
    First(L) = nullptr;
    Last(L) = nullptr;
}

address alokasi(Infotype X) {
    address P = new Elmlist;
    Info(P) = X;
    Next(P) = nullptr;
    Prev(P) = nullptr;
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = nullptr;
}

void printinfo(List L) {
    if (First(L) == nullptr) {
        cout << "List kosong" << endl;
        return;
    }
    
    address P = Last(L);
    while (P != nullptr) {
        cout << "no polisi : " << Info(P).nopol << endl;
        cout << "warna     : " << Info(P).warna << endl;
        cout << "tahun     : " << Info(P).thnbuat << endl;
        P = Prev(P);
    }
}

void insertlast(List &L, address P) {
    if (First(L) == nullptr) {
        First(L) = P;
        Last(L) = P;
    } else {
        Next(Last(L)) = P;
        Prev(P) = Last(L);
        Last(L) = P;
    }
}

address findElm(List L, string nopol) {
    address P = First(L);
    while (P != nullptr) {
        if (Info(P).nopol == nopol) {
            return P;
        }
        P = Next(P);
    }
    return nullptr;
}

void deleteFirst(List &L, address &P) {
    P = First(L);
    if (First(L) == Last(L)) {
        First(L) = nullptr;
        Last(L) = nullptr;
    } else {
        First(L) = Next(P);
        Prev(First(L)) = nullptr;
        Next(P) = nullptr;
    }
}

void deleteLast(List &L, address &P) {
    P = Last(L);
    if (First(L) == Last(L)) {
        First(L) = nullptr;
        Last(L) = nullptr;
    } else {
        Last(L) = Prev(P);
        Next(Last(L)) = nullptr;
        Prev(P) = nullptr;
    }
}

void deleteAfter(address Prec, address &P) {
    P = Next(Prec);
    address P_next = Next(P);
    
    Next(Prec) = P_next;
    Prev(P_next) = Prec;
    
    Next(P) = nullptr;
    Prev(P) = nullptr;
}

void deleteByNopol(List &L, string nopol) {
    address P = findElm(L, nopol);
    
    if (P == nullptr) {
        cout << "Data dengan nomor polisi " << nopol << " tidak ditemukan." << endl;
        return;
    }

    address P_deleted;
    if (P == First(L)) {
        deleteFirst(L, P_deleted);
    } else if (P == Last(L)) {
        deleteLast(L, P_deleted);
    } else {
        address Prec = Prev(P);
        deleteAfter(Prec, P_deleted);
    }
    
    cout << "Data dengan nomor polisi " << nopol << " berhasil dihapus." << endl;
    dealokasi(P_deleted);
}
```
### main.cpp
```c++
#include "doublylist.h"
#include <iostream>
#include <string>

using namespace std;

int main() {
    List L;
    CreateList(L);

    address P;
    Infotype data;
    string target;
    int pilihan;

    do {
        cout << "\nMENU\n";
        cout << "1. masukkan data kendaraan\n";
        cout << "2. cari data kendaraan\n";
        cout << "3. hapus data kendaraan\n";
        cout << "4. tampilkan semua data\n";
        cout << "0. keluar\n";
        cout << "pilih menu: ";
        cin >> pilihan;
        cin.ignore();

        switch (pilihan) {
            case 1:
                cout << "masukkan nomor polisi: ";
                getline(cin, data.nopol);
                
                if (findElm(L, data.nopol) != nullptr) {
                    cout << "nomor polisi sudah terdaftar" << endl;
                } else {
                    cout << "masukkan warna kendaraan: ";
                    getline(cin, data.warna);
                    cout << "masukkan tahun keluaran: ";
                    cin >> data.thnbuat;
                    cin.ignore();

                    P = alokasi(data);
                    insertlast(L, P);
                    cout << "Data berhasil ditambahkan." << endl;
                }
                break;
            case 2:
                cout << "masukkan nomor polisi yang dicari: ";
                getline(cin, target);
                
                P = findElm(L, target);
                if (P != nullptr) {
                    cout << "Data ditemukan:" << endl;
                    cout << "Nomor Polisi : " << Info(P).nopol << endl;
                    cout << "Warna        : " << Info(P).warna << endl;
                    cout << "Tahun        : " << Info(P).thnbuat << endl;
                } else {
                    cout << "Data dengan nomor polisi " << target << " tidak ditemukan." << endl;
                }
                break;
            case 3:
                cout << "masukkan nomor polisi yang akan dihapus: ";
                getline(cin, target);
                deleteByNopol(L, target);
                break;
            case 4:
                cout << "\nDATA LIST KENDARAAN (dari akhir ke awal):" << endl;
                printinfo(L);
                break;
            case 0:
                cout << "Keluar dari program..." << endl;
                break;
            default:
                cout << "Pilihan tidak valid." << endl;
                break;
        }

    } while (pilihan != 0);

    P = First(L);
    while (P != nullptr) {
        address temp = Next(P);
        dealokasi(P);
        P = temp;
    }

    return 0;
}
```
### 1. Buatlah ADT Doubly Linked list sebagai berikut di dalam file “Doublylist.h”:
```c++
Type infotype : kendaraan <
 nopol : string
 warna : string
 thnBuat : integer
>
Type address : pointer to ElmList
Type ElmList <
 info : infotype
 next :address
 prev : address
>
Type List <
 First : address
 Last : address
>
procedure CreateList( input/output L : List )
function alokasi( x : infotype ) → address
procedure dealokasi(input/output P : address )
procedure printInfo( input L : List )
procedure insertLast(input/output L : List, input P : address )
```
Buatlah implementasi ADT Doubly Linked list pada file “Doublylist.cpp” dan coba hasil implementasi ADT pada file “main.cpp”.


## Referensi

1. Modul 5: Singly Linked List (Bagian Kedua) [Modul Praktikum Struktur Data]. Telkom University, Bandung.
2. https://www.tutorialspoint.com/cplusplus-program-to-implement-singly-linked-list


