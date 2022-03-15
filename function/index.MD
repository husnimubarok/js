# Function

Apabila kita memiliki beberapa baris kode program yang sering kita gunakan, maka terdapat dua cara untuk menggunakannya:

1. Melakukan copy-paste baris kode program tersebut setiap kali kita memerlukannya.
1. Membuat sebuah function untuk "membungkus" kode program tersebut. Setiap saat kita memerlukan kode program tersebut, kita hanya perlu memanggil function yang telah kita buat sebelumnya.

Function merupakan kode program yang dikelompokkan menjadi satu bagian. Beberapa keuntungan dari penggunaan function adalah sebagai berikut:

- Kita tetap menganut prinsip DRY (Don't Repeat Yourself), sehingga human error akan diminimalisir.
- Ukuran kode program akan lebih kecil.
- Lebih mudah untuk melakukan debug.

> Sintaks
>
> ```js
> function nameFunction(parameter) {
>   // Kode program
> }
> ```
>
> `parameter` bersifat opsional.
>
> Contoh:
>
> ```js
> function penambahan() {
>   console.log(13 + 2);
>
> penambahan();
> ```
>
> &nbsp;

# Nama Function

Penamaan function pada JavaScript memiliki convention yang sama dengan penamaan variable:

- Hanya dapat menggunakan huruf, angka, \_ dan $.
- Menggunakan `camelCase` seperti: `balikString, cariMedian, cariRerata` dst. (best practice)
- Tidak menggunakan keyword yang sudah terpakai (reserved) oleh JavaScript itu sendiri sepert: `let, var, const, class` dll.
- Tidak boleh diawali dengan angka.
- tidak boleh menggunakan spasi.

# Parameters dan Argument

Apabila sebuah function kita deklarasikan dengan sebuah parameter kita dapa memanggil function tersebut dengan argument.

```js
// Membuat sebuah function penambahan dimana a dan b sebagai parameter.
function penambahan(a, b) {
  console.log(a + b);
}

// Memanggil function penambahan dengan argument 13 dan 2.
// 13 akan dikenali oleh function penambahan sebagai parameter a.
// 2 akan dikenali oleh function penambahan sebagai parameter b.
penambahan(13, 2);
```

Salah satu tujuan dari parameter adalah agar kode program dalam function menjadi dinamis. Kita dapat membuat kode program dalam function bekerja sesuai dengan argument saat kita memanggil function tersebut.

# Default Parameters

Parameter dunction dapat diberi nilai bawaan (default). Nilai tersebut akan digunakan apabila pada saat pemanggilan function kita tidak menyertakan nilai sebagai argument.

```js
function penambahan(a = 13, b = 3) {
  console.log(a + b);
}
penambahan(); // 16
penambahan(1, 5); // 6
```

Karena nilai argumen selalu dibaca dari kiri ke kanan sesuai dengan urutan parameter, maka parameter dengan nilai default akan selalu dituliskan di akhir. Contoh kasus apabila default parameter tidak diletakkan di akhir adalah seperti kode program di bawah:

```js
function tampilkan(x = 1, y) {
  console.log(x, y);
}

tampilkan(); // 1 undefined
tampilkan(2); // 2 undefined
```

# Return

Sebuah function dapat memberikan nilai kembalian(`return`). `return` dapat digunakan jika kita **hendak melakukan proses lebih lanjut terhadap data yang telah diolah oleh function**

```js
function penambahan(a, b) {
  let hasil = a + b;
  return hasil;
}

function perkalian(a, b) {
  let hasil = a * b;
  return hasil;
}
console.log(perkalian(penambahan(2, 3), penambahan(1, 2)));
```

Pada contoh program di atas, `return` dari function `penambahan` digunakan sebagai argument pemanggilan function `perkalian`. Kita tidak dapat menggunakan hasil dari function `penambahan` sebagai argument pemanggilan function `perkalian` jika kita **mengganti** return `hasil` dengan console.log(hasil)

> - Apabila eksekusi kode program pada function menemukan statement `return`, maka proses eksekusi function akan berhenti.

# Scope function

- Parameter yang disertakan saat proses deklarasi function **hanya akan dikenali di dalam scope function itu saja**

```js
function penambahan(a, b) {
  return a + b;
}
penambahan(5, 10);
console.log(a); //ReferenceError: a is not defined
```

- Variable yang dideklarasikan di dalam function **hanya akan dikenali di dalam scope function itu saja**

```js
function penambahan() {
  let a = 5;
  let b = 10;
  return a + b;
}
console.log(a); //ReferenceError: a is not defined
console.log(b); //ReferenceError: b is not defined
```
