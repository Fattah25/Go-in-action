# Go Quick-Start
## 2.1 *Program Structure*


> ### 2.1 Project Structure for the Application
>---
> cd $GOPATH/src/github.com/goinaction/code/chapter2
>- sample (folder)
>   - data (folder)
>       
>       data.json  -- mengandung list umpan data
>   - matchers (folder)
>     
>       rss.go -- Pencocokan untuk mencari umpan rss
>   - search (folder)
> 
>       default.go -- Pencocokan default untuk mencari data
>
>       feed.go -- Dukungan untuk membaca file data json
>
>       match.go -- Dukungan interface untuk menggunakan pencocokan yang berbeda
>
>       search.go -- Logika main program untuk melakukan pencarian
> 
>   main.go -- entery point program
>


Kode diatur ke dalam empat folder ini, yang di list dalam urutan abjad.
Folder **data** berisi dokumen **JSON** dari *data feed* yang akan diambil oleh program
dan diproses untuk mencocokkan istilah **pencarian**. Folder **matchers** berisi kode untuk
berbagai jenis *feed*/umpan yang didukung program. Saat ini program hanya mendukung
satu *matcher*/pencocok yang memproses umpan jenis **RSS**. Folder **search** berisi tugas
logika untuk menggunakan *matcher*/pencocokan yang berbeda untuk mencari konten. Pada *parent folder* yaitu **sample**, berisi file kode `main.go`, yang merupakan **entery point** untuk
program.

> penyedia data <--- pencocok <--- yang menentukan jenis pencocokkan <--- yang menjalankan / output



## 2.2 *Main Package*

*etery point*[^1] program dapat ditemukan di [main.go](sample/main.go) [⬅](./doc.md). Meskipun hanya ada 21 baris code, ada beberapa hal yang perlu kita sebutkan.

Setiap program Go yang menghasilkan *executable* file memiliki **dua fitur** berbeda. Salah satu dari fitur itu dapat ditemukan pada baris **18**. Di sana Anda dapat melihat fungsi `main` yang dideklarasikan. Agar *build tool* menghasilkan *executable*, fungsi `main` harus dideklarasikan, dan itu menjadi *entry point*[^1] program. Fitur **kedua** dapat ditemukan di baris **01**
dari program.

> ### line 01
>---
> ```go
> 01 package main`
>```

Jika `main function` tidak ada di `main package`, *build tool* tidak akan menghasilkan file yang dapat dieksekusi. Setiap file kode di Go termasuk dalam satu paket/*package*, dan **main.go** tidak terkecuali.
pahami bahwa *package* mendefinisikan **unit kode** yang dikompilasi
dan namanya membantu memberikan tingkat tipuan ke *identifier* yang dideklarasikan
di dalamnya, seperti *namespace*. Ini memungkinkan untuk membedakan pengidentifikasi/*identifier*
yang dideklarasikan dengan **nama yang sama persis** dalam *package* yang berbeda yang diimpor.

> ### line 01
>---
> ```go
>03 import (
>04	"log"
>05	"os"
>06
>07	_ "github.com/goinaction/code/chapter2/sample/matchers"
>08	search "github.com/goinaction/code/chapter2/sample/search"
>09 )
>```

`Import` berfungsi mengimpor kode dan memberi kita akses ke *identifier* seperti *types*,
*functions*, *constants*, dan *interfaces*. Dalam kasus ini, kode dalam file kode **main.go** merujuk pada fungsi `run` dari **search package**, berkat impor di baris **08**.

[^1]: titik masuk.
