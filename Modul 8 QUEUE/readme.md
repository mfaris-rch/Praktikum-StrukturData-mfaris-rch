# <h1 align="center">Laporan Praktikum Modul 8 <br> QUEUE
<p align="center">Muhammad Faris Rachmadi - 103112400079</p>

## Dasar Teori
Berdasarkan modul Anda, Queue (antrean) adalah struktur data linear yang diibaratkan seperti antrean pada loket tiket , di mana ia menganut prinsip dasar FIFO (First In, First Out). Prinsip ini berarti elemen yang pertama kali masuk ke dalam antrean adalah elemen yang juga akan pertama kali diakses atau dikeluarkan. Untuk menerapkan aturan ini, queue memiliki dua operasi utama: Insert (Enqueue), yaitu proses penyisipan elemen yang selalu dilakukan pada bagian akhir (disebut Tail), dan Delete (Dequeue), yaitu proses pengambilan atau penghapusan elemen yang selalu dilakukan pada bagian awal (disebut Head). Dalam implementasinya menggunakan bahasa C, struktur data queue ini dapat diwujudkan menggunakan tipe data array (tabel) maupun linked list.
## Guided

### Guided 1
```c++
#include <iostream>
using namespace std;

#define MAX 5 // ukuran maksimal queue

// Struktur Queue
struct Queue {
    int data[MAX];
    int head;
    int tail;
};

// Membuat antrean kosong
void createQueue(Queue &Q) {
    Q.head = -1;
    Q.tail = -1;
}

bool isEmpty(Queue Q) {
    return (Q.head == -1 && Q.tail == -1);
}

bool isFull(Queue Q) {
    return (Q.tail == MAX - 1);
}

// Menampilkan isi antrian
void printQueue(Queue Q) {
    if (isEmpty(Q)) {
        cout << "Queue kosong!" << endl;
    } else {
        cout << "Queue : ";
        for (int i = Q.head; i <= Q.tail; i++) {
            cout << Q.data[i] << " ";
        }
        cout << endl;
    }
}

void enqueue(Queue &Q, int x) {
    if (isFull(Q)) {
        cout << "Queue penuh! Tidak bisa menambah data." << endl;
    } else {
        if (isEmpty(Q)) {
            Q.head = Q.tail = 0;
        } else {
            Q.tail++;
        }
        Q.data[Q.tail] = x;
        cout << "Enqueue: " << x << endl;
    }
}

void dequeue(Queue &Q) {
    if (isEmpty(Q)) {
        cout << "Queue kosong! Tidak ada data yang dihapus." << endl;
    } else {
        cout << "Dequeue: " << Q.data[Q.head] << endl;
        // Jika hanya 1 elemen
        if (Q.head == Q.tail) {
            Q.head = Q.tail = -1;
        } else {
            // Geser semua elemen ke kiri
            for (int i = Q.head; i < Q.tail; i++) {
                Q.data[i] = Q.data[i + 1];
            }
            Q.tail--;
        }
    }
}

int main() {
    Queue Q;
    enqueue(Q, 5);
    enqueue(Q, 2);
    enqueue(Q, 7);
    printQueue(Q);

    dequeue(Q);
    printQueue(Q);

    enqueue(Q, 4);
    enqueue(Q, 9);
    printQueue(Q);

    dequeue(Q);
    dequeue(Q);
    printQueue(Q);

    return 0;
}
```
> Output
> ![alt](ouput/guided.png)
> Kode C++ ini adalah sebuah program yang mengimplementasikan struktur data Queue (antrean) menggunakan array statis dengan ukuran tetap (MAX = 5). Program ini mengelola antrean menggunakan dua indeks integer, head (penanda depan) dan tail (penanda belakang), yang diinisialisasi ke -1 untuk menandakan antrean kosong. Terdapat fungsi-fungsi dasar seperti createQueue (inisialisasi), isEmpty (cek kosong), isFull (cek penuh saat tail di MAX-1), enqueue (menambah elemen di tail), dan dequeue (menghapus elemen dari head). Implementasi dequeue pada kode ini menggunakan metode pergeseran elemen (shifting): setelah elemen di head diambil, semua elemen sisa di belakangnya digeser satu posisi ke depan, dan nilai tail dikurangi satu. Fungsi main kemudian mendemonstrasikan penggunaan antrean ini dengan melakukan beberapa kali operasi enqueue dan dequeue sambil mencetak isi antrean ke layar.
## UnGuided

## soal 1
Buatlah ADT Queue menggunakan ARRAY sebagai berikut di dalam file “queue.h”: 
```c++
Type infotype: integer 
Type Queue:  < 
info : array [5] of infotype {index array dalam C++ 
dimulai dari 0} 
head, tail : integer 
> 
procedure CreateQueue (input/output Q: Queue) 
function isEmptyQueue (Q: Queue) → boolean 
function isFullQueue (Q: Queue) → boolean 
procedure enqueue (input/output Q: Queue, input x: infotype)  
function dequeue (input/output Q: Queue) → infotype 
procedure printInfo (input Q: Queue)

```
## Buatlah implementasi ADT Queue pada file “queue.cpp” dengan menerapkan mekanisme 
queue  Alternatif 1 (head diam, tail bergerak).
```c++
int main() { 
cout << "Hello World" << endl; 
Queue Q; 
createQueue(Q); 
cout<<"----------------------"<<endl; 
cout<<" H - T \t | Queue info"<<endl; 
cout<<"----------------------"<<endl; 
printInfo(Q); 
enqueue(Q,5); printInfo(Q); 
enqueue(Q,2); printInfo(Q); 
enqueue(Q,7); printInfo(Q); 
dequeue(Q); printInfo(Q); 
enqueue(Q,4); printInfo(Q); 
dequeue(Q); printInfo(Q); 
dequeue(Q); printInfo(Q);
return 0;
}

```
### queue.h
```c++
#ifndef QUEUE_H
#define QUEUE_H

#include <iostream>
using namespace std;

const int MaxEl = 5; 

typedef int Infotype;

struct Queue {
    Infotype Info[MaxEl];
    int head;
    int tail;
};

#define Head(Q) (Q).head
#define Tail(Q) (Q).tail
#define Info(Q) (Q).Info

void CreateQueue(Queue &Q);
bool isEmpty(Queue Q);
bool isFull(Queue Q);
void enqueue(Queue &Q, Infotype x);
Infotype dequeue(Queue &Q);
void printInfo(Queue Q);

#endif
```

### queue.cpp(alternatif 1)
```c++
#include "queue.h"

void CreateQueue(Queue &Q) {
    Head(Q) = -1;
    Tail(Q) = -1;
}

bool isEmpty(Queue Q) {
    return Head(Q) == -1;
}

bool isFull(Queue Q) {
    return Tail(Q) == (MaxEl - 1);
}

void enqueue(Queue &Q, Infotype x) {
    if (isFull(Q)) {
    } else {
        if (isEmpty(Q)) {
            Head(Q) = 0;
        }
        Tail(Q)++;
        Info(Q)[Tail(Q)] = x;
    }
}

Infotype dequeue(Queue &Q) {
    Infotype x;
    
    if (isEmpty(Q)) {
        return -999;
    } else {
        x = Info(Q)[Head(Q)];
        
        for (int i = Head(Q); i < Tail(Q); i++) {
            Info(Q)[i] = Info(Q)[i + 1];
        }
        
        Tail(Q)--;
        
        if (Tail(Q) == -1) {
            Head(Q) = -1;
        }
        
        return x;
    }
}

void printInfo(Queue Q) {
    cout << Head(Q) << "\t-\t" << Tail(Q) << "\t! ";
    
    if (isEmpty(Q)) {
        cout << "empty queue";
    } else {
        cout << ": ";
        for (int i = Head(Q); i <= Tail(Q); i++) {
            cout << Info(Q)[i] << " ";
        }
    }
    cout << endl;
}
```
### main.cpp
```c++
#include <iostream>
#include "queue.h"

using namespace std;

int main() {
    cout << "Hello World" << endl;
    
    Queue Q;
    
    CreateQueue(Q);
    
    cout << "---------------------------------------" << endl;
    cout << "H\t-\tT\t| Queue Info" << endl;
    cout << "---------------------------------------" << endl;
    
    printInfo(Q);
    
    enqueue(Q, 5); 
    printInfo(Q);
    
    enqueue(Q, 2); 
    printInfo(Q);
    
    enqueue(Q, 7); 
    printInfo(Q);
    
    dequeue(Q); 
    printInfo(Q);
    
    enqueue(Q, 4); 
    printInfo(Q);
    
    dequeue(Q); 
    printInfo(Q);
    
    dequeue(Q); 
    printInfo(Q);
    
    dequeue(Q); 
    printInfo(Q);
    
    return 0;
}
```
> Output
> ![alt](ouput/soal1.png)
> Program C++ ini mengimplementasikan ADT Queue (antrian) menggunakan array dengan mekanisme "head diam". Pada pendekatan ini, head (kepala antrian) selalu ditahan di indeks 0, sementara tail (ekor antrian) bergerak maju seiring penambahan data (enqueue). Konsekuensi utama dari metode ini adalah setiap kali terjadi operasi dequeue (pengambilan data), elemen di indeks 0 diambil, dan semua elemen sisa di belakangnya harus digeser satu per satu ke kiri agar head tetap di posisi 0, yang membuat operasi dequeue menjadi kurang efisien jika antrian sangat panjang.


### Soal 2 
Buatlah implementasi ADT Queue pada file “queue.cpp” dengan menerapkan mekanisme 
queue  Alternatif 2 (head bergerak, tail bergerak). 
### queue.cpp(alternatif 2)
```C++
#include "queue.h"

void CreateQueue(Queue &Q) {
    Head(Q) = -1;
    Tail(Q) = -1;
}

bool isEmpty(Queue Q) {
    return Head(Q) == -1;
}

bool isFull(Queue Q) {
    return Tail(Q) == (MaxEl - 1);
}

void enqueue(Queue &Q, Infotype x) {
    if (isFull(Q)) {
    } else {
        if (isEmpty(Q)) {
            Head(Q) = 0;
        }
        Tail(Q)++;
        Info(Q)[Tail(Q)] = x;
    }
}

Infotype dequeue(Queue &Q) {
    Infotype x;
    
    if (isEmpty(Q)) {
        return -999;
    } else {
        x = Info(Q)[Head(Q)];
        
        Head(Q)++;
        
        if (Head(Q) > Tail(Q)) {
            CreateQueue(Q);
        }
        
        return x;
    }
}

void printInfo(Queue Q) {
    cout << Head(Q) << "\t-\t" << Tail(Q) << "\t! ";
    
    if (isEmpty(Q)) {
        cout << "empty queue";
    } else {
        cout << ": ";
        for (int i = Head(Q); i <= Tail(Q); i++) {
            cout << Info(Q)[i] << " ";
        }
    }
    cout << endl;
}
```
> Output
> ![alt](ouput/soal2.png)
> Program C++ ini mengimplementasikan ADT Queue menggunakan array dengan mekanisme "head bergerak dan tail bergerak" secara linear. Pada metode ini, enqueue akan menggerakkan tail ke kanan dan dequeue juga akan menggerakkan head ke kanan, sehingga tidak memerlukan pergeseran elemen yang lambat. Meskipun operasi enqueue dan dequeue sangat cepat, implementasi ini memiliki kelemahan signifikan yaitu boros memori; slot array yang telah ditinggalkan oleh head tidak dapat digunakan kembali, sehingga antrian bisa cepat dianggap 'penuh' saat tail mencapai akhir array, meskipun di bagian depannya masih banyak ruang kosong.


### Soal 3
Buatlah implementasi ADT Queue pada file “queue.cpp” dengan menerapkan mekanisme 
queue  Alternatif 3 (head dan tail berputar) 
### queue.cpp(alternatif 3)
```C++
#include "queue.h"

void CreateQueue(Queue &Q) {
    Head(Q) = -1;
    Tail(Q) = -1;
}

bool isEmpty(Queue Q) {
    return Head(Q) == -1;
}

int nbElmt(Queue Q) {
    if (isEmpty(Q)) {
        return 0;
    } else if (Tail(Q) >= Head(Q)) {
        return Tail(Q) - Head(Q) + 1;
    } else {
        return MaxEl - Head(Q) + Tail(Q) + 1;
    }
}

bool isFull(Queue Q) {
    return nbElmt(Q) == MaxEl;
}

void enqueue(Queue &Q, Infotype x) {
    if (isFull(Q)) {
    } else {
        if (isEmpty(Q)) {
            Head(Q) = 0;
            Tail(Q) = 0;
        } else {
            Tail(Q) = (Tail(Q) + 1) % MaxEl;
        }
        Info(Q)[Tail(Q)] = x;
    }
}

Infotype dequeue(Queue &Q) {
    Infotype x;
    
    if (isEmpty(Q)) {
        return -999;
    } else {
        x = Info(Q)[Head(Q)];
        
        if (Head(Q) == Tail(Q)) {
            CreateQueue(Q);
        } else {
            Head(Q) = (Head(Q) + 1) % MaxEl;
        }
        
        return x;
    }
}

void printInfo(Queue Q) {
    cout << Head(Q) << "\t-\t" << Tail(Q) << "\t! ";
    
    if (isEmpty(Q)) {
        cout << "empty queue";
    } else {
        cout << ": ";
        
        int i = Head(Q);
        int count = nbElmt(Q);
        
        while (count > 0) {
            cout << Info(Q)[i] << " ";
            i = (i + 1) % MaxEl;
            count--;
        }
    }
    cout << endl;
}
```
> Output
> ![alt](ouput/soal3.png)
> Program C++ ini mengimplementasikan ADT Queue (Alternatif 3), yang dikenal sebagai Circular Queue atau "antrian berputar". Ini adalah metode berbasis array yang paling efisien karena head dan tail dapat bergerak melintasi batas akhir array dan kembali lagi ke indeks 0, seolah-olah array tersebut melingkar. Dengan memanfaatkan operasi modulo (%) untuk menentukan posisi berikutnya, implementasi ini memanfaatkan semua slot array yang tersedia secara maksimal, menghindari pemborosan ruang yang terjadi di Alternatif 2 dan operasi pergeseran yang lambat di Alternatif 1.




## Referensi

1. Modul 8: Queue [Modul Praktikum Struktur Data]. Telkom University, Bandung.
2. https://www.programiz.com/cpp-programming/queue



