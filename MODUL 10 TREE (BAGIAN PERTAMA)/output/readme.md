# <h1 align="center">Laporan Praktikum Modul 10 <br> TREE (BAGIAN PERTAMA)
<p align="center">Muhammad Faris Rachmadi - 103112400079</p>

## Dasar Teori
Tree (pohon) adalah struktur data non-linear yang bersifat hierarkis, menggambarkan hubungan one-to-many antara elemen-elemennya menyerupai struktur pohon terbalik dengan satu elemen puncak yang disebut akar (root). Berbeda dengan struktur data linear seperti array atau stack, tree terdiri dari sekumpulan simpul (node) yang terhubung oleh sisi (edge), di mana setiap simpul dapat memiliki simpul induk (parent) dan nol atau lebih simpul anak (child); simpul yang tidak memiliki anak disebut daun (leaf). Jenis tree yang paling fundamental dan sering dipelajari adalah Binary Tree (Pohon Biner), di mana setiap simpul dibatasi maksimal memiliki dua anak (anak kiri dan anak kanan), yang memungkinkan operasi penyimpanan dan penelusuran data (traversal)—seperti PreOrder, InOrder, dan PostOrder—dilakukan secara lebih efisien dibandingkan struktur linear.
## Guided

### Guided 1
```c++
#include <iostream>
#include <string>

using namespace std;
struct Node {
    int data;
    Node *kiri, *kanan ;
};

Node *buatNode(int nilai) {
    Node *baru = new Node();
    baru->data = nilai;
    baru->kiri = baru->kanan = NULL;
    return baru;
}

Node *insert(Node *root, int nilai) {
    if (root == NULL)
        return buatNode(nilai);
    if (nilai < root->data)
        root->kiri = insert(root->kiri, nilai);
    else if (nilai > root->data)
        root->kanan = insert(root->kanan, nilai);

    return root;
}

Node *search(Node *root, int nilai) {
    if (root == NULL || root->data == nilai)
        return root;

    if (nilai < root->data)
        return search(root->kiri, nilai);

    return search(root->kanan, nilai);
}

Node *nilaiTerkecil(Node *root) {
    Node *current = root;
    while (current && current->kiri != NULL)
        current = current->kiri;
    return current;
}

Node *hapus(Node *root, int nilai) {
    if (root == NULL)
        return root;

    if (nilai < root->data)
        root->kiri = hapus(root->kiri, nilai);
    else if (nilai > root->data)
        root->kanan = hapus(root->kanan, nilai);
    else {
        if (root->kiri == NULL) {

            Node *temp = root->kanan;
            delete root;
            return temp;

        } else if (root->kanan == NULL) {

            Node *temp = root->kiri;
            delete root;
            return temp;
        }

        Node *temp = nilaiTerkecil(root->kanan);
        root->data = temp->data;
        root->kanan = hapus(root->kanan, temp->data);
    }
    return root;
}

Node *update(Node *root, int lama, int baru) {
    Node *found = search(root, lama);
    if (found != NULL) {
        root = hapus(root, lama);
        root = insert(root, baru);
        cout << "Data " << lama << " telah diupdate menjadi " << baru << "." << endl;
    } else {
        cout << "data " << lama << " tidak ditemukan." << endl;
    }
    return root;
}

void preOrder(Node *root) {
    if (root != NULL) {
        cout << root->data << " ";
        preOrder(root->kiri);
        preOrder(root->kanan);
    }
}

void inOrder(Node *root) {
    if (root != NULL) {
        inOrder(root->kiri);
        cout << root->data << " ";
        inOrder(root->kanan);
    }
}

void postOrder(Node *root) {
    if (root != NULL) {
        postOrder(root->kiri);
        postOrder(root->kanan);
        cout << root->data << " ";
    }
}

int main() {
    Node *root = NULL;

    cout << "--- 1. INSERT DATA ---" << endl;
    root = insert(root, 10);
    root = insert(root, 5);
    root = insert(root, 20);
    root = insert(root, 3);
    root = insert(root, 7);
    root = insert(root, 15);
    root = insert(root, 25);
    cout << "Data berhasil dimasukant. \n"
        << endl;

    cout << "--- 2. TAMPILKAN TREE (TRAVERSAL) ---" << endl;
    cout << "PreOrder: ";
    preOrder(root);
    cout << endl;
    cout << "InOrder: ";
    inOrder(root);
    cout << endl;
    cout << "PostOrder: ";
    postOrder(root);
    cout << "\n"
        << endl;

    cout << "--- 3. TEST SEARCH ---" << endl;
    int cari1 = 7, cari2 = 99;
    cout << "Cari " << cari1 << ": " << (search(root, cari1) ? "Ditemukan" : "Tidak Ada") << endl;
    cout << "Cari " << cari2 << ": " << (search(root, cari2) ? "Ditemukan" : "Tidak Ada") << endl;
    cout << endl;

    cout << "--- 4. TEST UPDATE ---" << endl;
    root = update(root, 5, 8);
    cout << " Hasil InOrder setelah update: ";
    cout << endl;
    cout << endl;

    cout << "PreOrder: ";
    preOrder(root);
    cout << endl;
    cout << "InOrder: ";
    inOrder(root);
    cout << endl;
    cout << "PostOrder: ";
    postOrder(root);
    cout << "\n"
         << endl;

    cout << "--- 5. TEST DELETE ---" << endl;
    cout << "Menghapus angka 20..." << endl;
    root = hapus(root, 20);

    cout << "PreOrder : ";
    preOrder(root);
    cout << endl;
    cout << "InOrder : ";
    inOrder(root);
    cout << endl;
    cout << "PostOrder : ";
    postOrder(root);
    cout << "\n"
            << endl;
    
    return 0;
}
```
> Output
> ![alt](ouput/guided.png)
> Program C++ ini mengimplementasikan struktur data Binary Search Tree (BST) lengkap yang memungkinkan pengelolaan data dinamis melalui operasi penyisipan (`insert`), pencarian (`search`), penghapusan (`hapus`), dan pembaruan (`update`) nilai. Logika utamanya memanfaatkan fungsi rekursif untuk menempatkan angka yang lebih kecil di cabang kiri dan angka yang lebih besar di cabang kanan, serta menangani kasus penghapusan node yang kompleks (terutama node dengan dua anak) dengan menggantinya menggunakan nilai terkecil dari sub-pohon kanan. Selain itu, program ini menyediakan fitur pembaruan data dengan mekanisme menghapus nilai lama lalu menyisipkan nilai baru untuk menjaga keterurutan pohon, dan diakhiri dengan fungsi `main` yang mendemonstrasikan seluruh operasi tersebut serta menampilkannya melalui metode penelusuran (*traversal*) PreOrder, InOrder, dan PostOrder.
## UnGuided

## soal 1
1. Buatlah ADT Binary Search Tree menggunakan Linked list sebagai berikut di dalam file 
“bstree.h”:
```pseudocode
Type infotype: integer  
Type address : pointer to Node 
Type Node:  < 
info : infotype 
left, right : address 
> 
function alokasi( x : infotype ) → address 
procedure insertNode( input/output root : address,  
input x : infotype ) 
function findNode( x : infotype, root : address )→address 
procedure printInorder( input root : address ) 

```
Buatlah implementasi ADT Binary Search Tree pada file “bstree.cpp” dan cobalah hasil implementasi ADT pada file “main.cpp” 
```c++
#include <iostream> 
#include "bstree.h" 
using namespace std;  
int main() { 
cout << "Hello World" << endl; 
address root = Nil; 
insertNode(root,1); 
insertNode(root,2); 
insertNode(root,6); 
insertNode(root,4); 
insertNode(root,5); 
insertNode(root,3); 
insertNode(root,6); 
insertNode(root,7); 
InOrder(root); 
return 0; 
} 

```

### Soal 2 
2. Buatlah fungsi untuk menghitung jumlah node dengan fungsi berikut. 
➢ fungsi hitungJumlahNode( root:address ) : integer 
/* fungsi mengembalikan integer banyak node yang ada di dalam BST*/ 
➢ fungsi hitungTotalInfo( root:address, start:integer ) : integer 
/* fungsi mengembalikan jumlah (total) info dari node-node yang ada di dalam BST*/ 
➢ fungsi hitungKedalaman( root:address, start:integer ) : integer
/* fungsi rekursif mengembalikan integer kedalaman maksimal dari binary tree */ 
```C++
int main() { 
cout << "Hello World" << endl; 
address root = Nil; 
insertNode(root,1); 
insertNode(root,2); 
insertNode(root,6); 
insertNode(root,4); 
insertNode(root,5); 
insertNode(root,3); 
insertNode(root,6); 
insertNode(root,7); 
InOrder(root); 
cout<<"\n"; 
cout<<"kedalaman : "<<hitungKedalaman(root,0)<<endl; 
cout<<"jumlah Node : "<<hitungNode(root)<<endl; 
cout<<"total : "<<hitungTotal(root)<<endl; 
return 0; 
}
```


### Soal 3
3. Print tree secara pre-order dan post-order.
   
### Jawaban
## bstree.h
```C++
#ifndef BSTREE_H
#define BSTREE_H

#include <iostream>
using namespace std;

typedef int infotype;
typedef struct Node *address;

struct Node {
    infotype info;
    address left;
    address right;
};

address alokasi(infotype x);
void insertNode(address &root, infotype x);
address findNode(infotype x, address root);
void printInOrder(address root);
void printPreOrder(address root);
void printPostOrder(address root);

int hitungJumlahNode(address root);
int hitungTotalInfo(address root);
int hitungKedalaman(address root);

#endif
```
## bstree.cpp
```C++
#include "bstree.h"

address alokasi(infotype x) {
    address P = new Node;
    P->info = x;
    P->left = NULL;
    P->right = NULL;
    return P;
}

void insertNode(address &root, infotype x) {
    if (root == NULL) {
        root = alokasi(x);
    } else {
        if (x < root->info) {
            insertNode(root->left, x);
        } else if (x > root->info) {
            insertNode(root->right, x);
        }
    }
}

address findNode(infotype x, address root) {
    if (root == NULL) return NULL;
    if (root->info == x) return root;
    if (x < root->info) return findNode(x, root->left);
    return findNode(x, root->right);
}

void printInOrder(address root) {
    if (root != NULL) {
        printInOrder(root->left);
        cout << root->info << " - ";
        printInOrder(root->right);
    }
}

void printPreOrder(address root) {
    if (root != NULL) {
        cout << root->info << " - ";
        printPreOrder(root->left);
        printPreOrder(root->right);
    }
}

void printPostOrder(address root) {
    if (root != NULL) {
        printPostOrder(root->left);
        printPostOrder(root->right);
        cout << root->info << " - ";
    }
}

int hitungJumlahNode(address root) {
    if (root == NULL) return 0;
    return 1 + hitungJumlahNode(root->left) + hitungJumlahNode(root->right);
}

int hitungTotalInfo(address root) {
    if (root == NULL) return 0;
    return root->info + hitungTotalInfo(root->left) + hitungTotalInfo(root->right);
}

int max(int a, int b) {
    return (a > b) ? a : b;
}

int hitungKedalaman(address root) {
    if (root == NULL) return 0;
    return 1 + max(hitungKedalaman(root->left), hitungKedalaman(root->right));
}
```
## main.cpp
```C++
#include <iostream>
#include "bstree.h"

using namespace std;

int main() {
    address root = NULL;
    
    cout << "Hello World" << endl;

    insertNode(root, 6);
    insertNode(root, 4);
    insertNode(root, 7);
    insertNode(root, 2);
    insertNode(root, 5);
    insertNode(root, 1);
    insertNode(root, 3);

    cout << "\nInOrder   : ";
    printInOrder(root);
    cout << endl;

    cout << "PreOrder  : ";
    printPreOrder(root);
    cout << endl;
    
    cout << "PostOrder : ";
    printPostOrder(root);
    cout << endl;

    cout << endl;

    cout << "Kedalaman   : " << hitungKedalaman(root) << endl;
    cout << "Jumlah Node : " << hitungJumlahNode(root) << endl;
    cout << "Total Info  : " << hitungTotalInfo(root) << endl;

    return 0;
}

```
> Output
> ![alt](ouput/soal3.png)
> Program C++ ini mengimplementasikan ADT Queue (Alternatif 3), yang dikenal sebagai Circular Queue atau "antrian berputar". Ini adalah metode berbasis array yang paling efisien karena head dan tail dapat bergerak melintasi batas akhir array dan kembali lagi ke indeks 0, seolah-olah array tersebut melingkar. Dengan memanfaatkan operasi modulo (%) untuk menentukan posisi berikutnya, implementasi ini memanfaatkan semua slot array yang tersedia secara maksimal, menghindari pemborosan ruang yang terjadi di Alternatif 2 dan operasi pergeseran yang lambat di Alternatif 1.




## Referensi

1. Modul 8: Queue [Modul Praktikum Struktur Data]. Telkom University, Bandung.
2. https://www.programiz.com/cpp-programming/queue




