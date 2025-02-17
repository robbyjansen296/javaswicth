/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

 package com.mycompany.projectservicemotor;

 import java.util.Scanner;
 
 /**
  *
  * @author ASUS-ROG
  */
 public class Projectservicemotor {
      // Harga masing-masing layanan
     static final int HARGA_GANTI_OLI = 50000;
     static final int HARGA_CEK_REM = 30000;
     static final int HARGA_GANTI_BAN = 150000;
     static final int HARGA_CEK_RANTAI = 20000;
     static final int HARGA_CEK_AKI = 25000;
  
  public static void main(String[] args) {
         // Menampilkan pilihan jenis service
         try ( // Menampilkan menu layanan
         // Membuat objek Scanner untuk mengambil input dari pengguna
                 Scanner scanner = new Scanner(System.in)) {
             // Menampilkan pilihan jenis service
             System.out.println("Pilih jenis layanan service motor:");
             System.out.println("1. Service Kecil");
             System.out.println("2. Service Besar");
             System.out.print("Masukkan nomor pilihan layanan (1-2): ");
             int pilihanJenisService = scanner.nextInt();
             // Variabel untuk menyimpan total harga dan layanan yang dipilih
             int totalHarga = 0;
             String layanan = "";
             // Menentukan service yang dipilih oleh pengguna
             if (pilihanJenisService == 1) {
                 // Service Kecil
                 System.out.println("\nPilih layanan untuk Service Kecil:");
                 System.out.println("1. Ganti Oli");
                 System.out.println("2. Periksa Rem");
                 System.out.println("3. Cek Kondisi Ban");
                 System.out.println("4. Cuci Motor");
                 System.out.print("Masukkan nomor pilihan layanan (1-4): ");
                 
                 int pilihanKecil = scanner.nextInt();
                 
                 // Menggunakan switch untuk menentukan layanan kecil yang dipilih
                 switch (pilihanKecil) {
                     case 1 -> {
                         layanan = "Ganti Oli";
                         totalHarga = 50000;
                     }
                     case 2 -> {
                         layanan = "Periksa Rem";
                         totalHarga = 30000;
                     }
                     case 3 -> {
                         layanan = "Cek Kondisi Ban";
                         totalHarga = 25000;
                     }
                     case 4 -> {
                         layanan = "Cuci Motor";
                         totalHarga = 20000;
                     }
                     default -> {
                         System.out.println("Pilihan tidak valid! Silakan pilih antara 1 hingga 4.");
                         return;  // Keluar dari program jika pilihan tidak valid
                     }
                 }
             } else if (pilihanJenisService == 2) {
                 // Service Besar
                 System.out.println("\nPilih layanan untuk Service Besar:");
                 System.out.println("1. Service Besar (Ganti Oli + Cek Kelistrikan + Periksa Mesin)");
                 System.out.println("2. Service Besar (Cek Kelistrikan + Ganti Oli + Periksa Rem)");
                 System.out.print("Masukkan nomor pilihan layanan (1-2): ");
                 
                 int pilihanBesar = scanner.nextInt();
                 
                 // Menggunakan switch untuk menentukan layanan besar yang dipilih
                 switch (pilihanBesar) {
                     case 1 -> {
                         layanan = "Service Besar (Ganti Oli + Cek Kelistrikan + Periksa Mesin)";
                         totalHarga = 200000;
                     }
                     case 2 -> {
                         layanan = "Service Besar (Cek Kelistrikan + Ganti Oli + Periksa Rem)";
                         totalHarga = 175000;
                     }
                     default -> {
                         System.out.println("Pilihan tidak valid! Silakan pilih antara 1 hingga 2.");
                         return;  // Keluar dari program jika pilihan tidak valid
                     }
                 }
             } else {
                 System.out.println("Pilihan tidak valid! Silakan pilih antara 1 dan 2.");
                 return;  // Keluar dari program jika pilihan tidak valid
             }   // Menampilkan struk
             System.out.println("\n==================== STRUK LAYANAN ====================");
             System.out.println("Layanan yang dipilih: " + layanan);
             System.out.println("Harga layanan: Rp " + totalHarga);
             System.out.println("=========================================================");
             System.out.println("Total Tagihan: Rp " + totalHarga);
             System.out.println("=========================================================");
             // Menu Pembayaran
             System.out.println("\nPilih metode pembayaran:");
             System.out.println("1. Tunai");
             System.out.println("2. Transfer Bank");
             System.out.println("3. E-wallet");
             System.out.print("Masukkan nomor pilihan metode pembayaran (1-3): ");
             int metodePembayaran = scanner.nextInt();
             switch (metodePembayaran) {
                 case 1 -> {
                     System.out.println("\nAnda memilih pembayaran dengan **Tunai**.");
                     System.out.print("Masukkan jumlah uang yang dibayar: Rp ");
                     int uangTunai = scanner.nextInt();
                     if (uangTunai < totalHarga) {
                         System.out.println("Uang yang Anda bayar kurang. Silakan bayar dengan jumlah yang tepat.");
                     } else {
                         int kembalian = uangTunai - totalHarga;
                         System.out.println("Pembayaran berhasil! Kembalian: Rp " + kembalian);
                     }
                 }
                 case 2 -> {
                     System.out.println("\nAnda memilih pembayaran dengan **Transfer Bank**.");
                     System.out.println("Silakan transfer sejumlah Rp " + totalHarga + " ke rekening berikut: ");
                     System.out.println("Rekening Bank: 123-456-789 (A/N: Robby jansen)");
                     System.out.println("Transfer berhasil jika Anda sudah mentransfer jumlah yang tepat.");
                 }
                 case 3 -> {
                     System.out.println("\nAnda memilih pembayaran dengan **E-wallet**.");
                     System.out.println("Silakan bayar menggunakan aplikasi E-wallet Anda dengan nominal Rp " + totalHarga + ".");
                     System.out.println("Pembayaran berhasil jika transaksi selesai di aplikasi.");
                 }
                 default -> {
                     System.out.println("Pilihan pembayaran tidak valid! Silakan pilih antara 1 hingga 3.");
                     return;  // Keluar dari program jika pilihan tidak valid
                 }
             }
             // Menutup scanner setelah penggunaan
         }
     }
 }
