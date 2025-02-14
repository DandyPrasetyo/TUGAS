1. PENJELASAN
   Program ini merupakan aplikasi berbasis teks untuk pemrosesan pemesanan di kafe. Pengguna dapat melihat menu, menambahkan pesanan, melihat daftar pesanan, menghitung total biaya, dan mengakhiri pemesanan.

2. FUNGSI SETIAP BAGIAN KODE

- import java.util.ArrayList; ArrayList → Digunakan untuk menyimpan daftar pesanan dan harga pesanan.
- import java.util.Scanner; Scanner → Digunakan untuk membaca input dari pengguna.

3. DEKLARASI DAN OBJEK SCANNER

public class CaffeKelompok8 {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);

- Kelas CaffeKelompok8 adalah kelas utama yang menjalankan program.
- Objek scanner dibuat untuk menerima input pengguna dari keyboard.

3. Deklarasi ArrayList untuk Menyimpan Pesanan

ArrayList<String> pesanan = new ArrayList<>(); //pesanan → Menyimpan daftar item yang dipesan.
ArrayList<Integer> harga = new ArrayList<>(); //harga → Menyimpan harga dari setiap pesanan

4. Daftar Menu dan Harga

String[] menu = {"Nasi Goreng - Rp20000", "Mie Goreng - Rp15000", "Roti Bakar - Rp12000",
"Kentang Goreng - Rp10000", "Teh Tarik - Rp8000", "Cappucino - Rp20000",
"Chocolate Ice - Rp25000"};
int[] hargaMenu = {20000, 15000, 12000, 10000, 8000, 20000, 25000};

- menu → Array yang menyimpan daftar menu beserta harga dalam bentuk string.
- hargaMenu → Array angka yang menyimpan harga masing-masing menu

5.  Perulangan Menu Utama
    while (true) { //Perulangan tak terbatas (while (true)) digunakan agar program berjalan terus hingga pengguna memilih opsi "Selesai"

6.  Menampilkan Menu
    System.out.println("=== Selamat Datang di Kafe ===");
    System.out.println("=== Menu ===");
    for (int i = 0; i < menu.length; i++) {
    System.out.println((i + 1) + ". " + menu[i]);
    }
    //Menampilkan daftar menu dengan nomor indeks dari 1 hingga jumlah menu

7.  Menampilkan Opsi Pilihan
    System.out.println("\nPilih opsi berikut:");
    System.out.println("1. Tambah Pesanan");
    System.out.println("2. Lihat Daftar Pesanan");
    System.out.println("3. Hitung Total Biaya");
    System.out.println("4. Selesai");
    //Memberikan opsi interaksi kepada pengguna:
    Tambah Pesanan

- Lihat Daftar Pesanan
- Hitung Total Biaya
- Keluar dari program

8.  Meminta Input dari Pengguna
    System.out.print("Masukkan pilihan Anda: ");
    int pilihan = scanner.nextInt();
    scanner.nextLine();
    // Meminta input angka untuk memilih opsi.
    // scanner.nextLine(); digunakan untuk menghindari bug input setelah penggunaan scanner.nextInt();.

9.  Menangani Opsi Tambah Pesanan
    if (pilihan == 1) {
    System.out.print("Masukkan nomor menu yang ingin dipesan: ");
    int nomorMenu = scanner.nextInt();
    System.out.print("Masukkan jumlah pesanan: ");
    int jumlah = scanner.nextInt();
    scanner.nextLine();

         if (nomorMenu >= 1 && nomorMenu <= menu.length) {
             pesanan.add(menu[nomorMenu - 1] + " x" + jumlah);
             harga.add(hargaMenu[nomorMenu - 1] * jumlah);
             System.out.println(menu[nomorMenu - 1] + " berhasil ditambahkan ke pesanan.\n");
         } else {
             System.out.println("Menu tidak valid.\n");
         }

    }

    - Meminta input nomor menu & jumlah pesanan.
    - Memeriksa apakah nomor menu valid.
    - Menambahkan pesanan ke dalam ArrayList.

10. Menampilkan Daftar Pesanan
    else if (pilihan == 2) {
    System.out.println("=== Daftar Pesanan ===");
    int totalSementara = 0;
    for (int i = 0; i < pesanan.size(); i++) {
    System.out.println((i + 1) + ". " + pesanan.get(i) + " - Rp" + harga.get(i));
    totalSementara += harga.get(i);
    }
    System.out.println("Total Biaya Sementara: Rp" + totalSementara + "\n");
    }

- Menampilkan daftar pesanan yang telah dimasukkan.
- Menghitung total biaya sementara.

12. Menghitung Total Biaya Akhir
    else if (pilihan == 3) {
    int totalBiaya = 0;
    for (int h : harga) {
    totalBiaya += h;
    }
    System.out.println("Total biaya seluruh pesanan: Rp" + totalBiaya + "\n");
    }

// Menjumlahkan seluruh harga dalam ArrayList harga.
// Menampilkan total biaya akhir.

13. Menutup Progam
    else if (pilihan == 4) {
    System.out.println("Terima kasih telah memesan di kafe kami!");
    break;
    }

//Keluar dari loop jika pengguna memilih opsi "Selesai".
//Menampilkan pesan terima kasih. 13. Menangani Input Tidak Valid
else {
System.out.println("Pilihan tidak valid. Silakan coba lagi.\n");
}

//Menampilkan pesan error jika input tidak valid

14. Menutup Scanner  
    scanner.close(); //Menutup Scanner untuk menghindari kebocoran sumber daya
