# <h1 align="center">Laporan Praktikum Modul 7 <br> STACK
<p align="center">Muhammad Faris Rachmadi - 103112400079</p>

## Dasar Teori
Stack (tumpukan) adalah salah satu bentuk struktur data linear yang menerapkan prinsip operasi seperti tumpukan benda, di mana elemen data diletakkan dan diambil hanya dari satu ujung. Prinsip fundamental yang digunakan oleh stack dikenal sebagai LIFO (Last In First Out), yang berarti elemen yang terakhir kali dimasukkan ke dalam tumpukan akan menjadi elemen yang pertama kali dikeluarkan. Akses terhadap data dalam stack bersifat terbatas dan hanya dapat dilakukan pada elemen paling awal atau paling atas, yang disebut sebagai "TOP". Terdapat dua operasi utama dalam stack: Push, yaitu operasi untuk menyisipkan atau menambahkan elemen baru ke posisi TOP (mirip dengan insert first pada list) , dan Pop, yaitu operasi untuk mengambil atau menghapus elemen yang berada di posisi TOP (mirip dengan delete first pada list).
## Guided

### Guided 1
```c++
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node *next;
};

bool isEmpty(Node *top)
{
    return top == nullptr;
}

void push(Node *&top, int data)
{
    Node *newNode = new Node();
    newNode->data = data;
    newNode->next = top;
    top = newNode;
}

int pop(Node *&top)
{
    if (isEmpty(top))
    {
        cout << "Stack kosong, tidak bisa pop!" << endl;
        return 0;
    }

    int poppedData = top->data;
    Node *temp = top;
    top = top->next;
    
    delete temp;
    return poppedData;
}

void show(Node *top)
{
    if (isEmpty(top))
    {
        cout << "Stack kosong." << endl;
        return;
    }

    cout << "TOP -> ";
    Node *temp = top;

    while (temp != nullptr)
    {
        cout << temp->data << " -> ";
        temp = temp->next;
    }

    cout << "NULL" << endl;
}

int main()
{
    Node *stack = nullptr;

    push(stack, 10);
    push(stack, 20);
    push(stack, 30);

    cout << "Menampilkan isi stack:" << endl;
    show(stack);

    cout << "Pop: " << pop(stack) << endl;

    cout << "Menampilkan sisa stack:" << endl;
    show(stack);

    return 0;
}
```
> Output
> ![alt](output/guided.png)
> Program ini adalah implementasi struktur data stack (tumpukan) dalam C++ yang menggunakan representasi linked list dinamis. Program mendefinisikan struct Node untuk menyimpan data integer dan sebuah pointer next yang menunjuk ke node berikutnya. Terdapat empat fungsi utama: isEmpty yang memeriksa apakah pointer top menunjuk ke nullptr, push yang menambahkan elemen baru ke puncak stack dengan membuat node baru, pop yang mengambil data sekaligus menghapus node teratas (menggunakan delete untuk mencegah kebocoran memori), dan show yang mencetak isi stack dari TOP ke NULL. Fungsi main kemudian mendemonstrasikan cara kerja stack dengan menginisialisasi stack kosong, melakukan push pada angka 10, 20, dan 30, menampilkannya, lalu melakukan satu kali pop dan menampilkan sisa isi stack.
## UnGuided

### stack.h
```c++
#ifndef STACK_H
#define STACK_H

#include <iostream>

using namespace std;

const int MaxEl = 20; 

typedef int Infotype;

struct Stack {
    Infotype T[MaxEl + 1];
    int TOP;
};

#define Top(S) (S).TOP
#define InfoTop(S) (S).T[(S).TOP]

void CreateStack(Stack &S);
bool isEmpty(Stack S);
bool isFull(Stack S);
void push(Stack &S, Infotype x);
Infotype pop(Stack &S);
void printInfo(Stack S);
void balikStack(Stack &S);

void pushAscending(Stack &S, Infotype x);

void getInputStream(Stack &S);

#endif
```

### stack.cpp
```c++
#include "stack.h"

void CreateStack(Stack &S) {
    Top(S) = -1;
}

bool isEmpty(Stack S) {
    return Top(S) == -1;
}

bool isFull(Stack S) {
    return Top(S) == MaxEl;
}

void push(Stack &S, Infotype x) {
    if (!isFull(S)) {
        Top(S)++;
        InfoTop(S) = x;
    } else {
        cout << "Stack penuh" << endl;
    }
}

Infotype pop(Stack &S) {
    Infotype x;
    if (!isEmpty(S)) {
        x = InfoTop(S);
        Top(S)--;
    } else {
        x = -999; 
    }
    return x;
}

void printInfo(Stack S) {
    cout << "[TOP] ";
    if (!isEmpty(S)) {
        for (int i = Top(S); i >= 0; i--) {
            cout << S.T[i] << " ";
        }
    }
    cout << endl;
}

void balikStack(Stack &S) {
    Stack S_temp;
    CreateStack(S_temp);

    while (!isEmpty(S)) {
        push(S_temp, pop(S));
    }
    
    S = S_temp; 
}

void pushAscending(Stack &S, Infotype x) {
    Stack S_temp;
    CreateStack(S_temp);

    while (!isEmpty(S) && InfoTop(S) > x) {
        push(S_temp, pop(S));
    }
    
    push(S, x);
    
    while (!isEmpty(S_temp)) {
        push(S, pop(S_temp));
    }
}

void getInputStream(Stack &S) {
    char c;
    Infotype x;

    while ((c = cin.get()) != '\n') {
        x = c - '0'; 
        push(S, x);
    }
}
```
### main.cpp
```c++
#include "stack.h"
#include <iostream>

using namespace std;

int main() {

    cout << "Hello world!" << endl;
    
    Stack S1;
    CreateStack(S1);
    
    push(S1, 3);
    push(S1, 4);
    push(S1, 8);
    pop(S1);
    push(S1, 2);
    push(S1, 3);
    pop(S1);
    push(S1, 9);
    
    printInfo(S1);
    
    cout << "balik stack" << endl;
    balikStack(S1);
    
    printInfo(S1);
    cout << "----------------------------------------" << endl;


    cout << "\nHello world!" << endl;
    
    Stack S2;
    CreateStack(S2);
    
    pushAscending(S2, 3);
    pushAscending(S2, 4);
    pushAscending(S2, 8);
    pushAscending(S2, 2);
    pushAscending(S2, 3);
    pushAscending(S2, 9);

    printInfo(S2);
    
    cout << "balik stack" << endl;
    balikStack(S2);
    
    printInfo(S2);
    cout << "----------------------------------------" << endl;


    cout << "\nHello world!" << endl;

    Stack S3;
    CreateStack(S3);
    getInputStream(S3);
    printInfo(S3);
    
    cout << "balik stack" << endl;
    balikStack(S3);
    
    printInfo(S3);
    cout << "----------------------------------------" << endl;
    
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
> Output no 1
> ![alt](output/soal1.png)
> ![alt](output/soal01.png)

### 2.Carilah elemen dengan nomor polisi D001 dengan membuat fungsi baru.
fungsi findElm( L : List, x : infotype ) : address
> Output no 2
> ![alt](output/soal2.png)

### 3.Hapus elemen dengan nomor polisi D003 dengan procedure delete.
- procedure deleteFirst( input/output L : List, P : address )
- procedure deleteLast( input/output L : List, P : address )
- procedure deleteAfter( input Prec : address, input/output P : address )
> Output no 3
> ![alt](output/soal3.png)
> program C++ ini berfungsi sebagai sistem manajemen data kendaraan menggunakan struktur data doubly linked list. Program ini menyediakan menu sederhana bagi pengguna untuk berinteraksi dengan daftar data, memungkinkan mereka untuk menambahkan data kendaraan baru (sekaligus mencegah duplikasi nomor polisi), mencari data berdasarkan nomor polisi, menghapus data yang ada, dan menampilkan keseluruhan daftar kendaraan yang tersimpan, dimulai dari data yang paling terakhir dimasukkan.



## Referensi

1. Modul 6: Doubly Linked List (Bagian Pertama) [Modul Praktikum Struktur Data]. Telkom University, Bandung.
2. (https://www.programiz.com/dsa/doubly-linked-list)



