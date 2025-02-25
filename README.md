/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.servicemotorjdk;

import java.util.Scanner;

/**
 *
 * @author ASUS-ROG
 */
public class Servicemotorjdk {
    static final int HARGA_GANTI_OLI = 50000;
    static final int HARGA_CEK_REM = 30000;
    static final int HARGA_GANTI_BAN = 150000;
    static final int HARGA_CEK_RANTAI = 20000;

    public static void main(String[] args) {
        try (Scanner scanner = new Scanner(System.in)) {
            boolean continueTransaction = true;  // Flag to continue or exit the program

            while (continueTransaction) {
                int totalHarga = 0;
                StringBuilder selectedServices = new StringBuilder();

                // Service selection process
                boolean continueService = true;  // Flag to continue or exit the service selection
                while (continueService) {
                    System.out.println("Pilih jenis layanan service motor:");
                    System.out.println("1. Service Kecil");
                    System.out.println("2. Service Besar");
                    System.out.print("Masukkan nomor pilihan layanan (1-2): ");
                    int serviceTypeChoice = scanner.nextInt();

                    switch (serviceTypeChoice) {
                        case 1 -> // Service Kecil
                            totalHarga = processServiceKecil(scanner, selectedServices, totalHarga);
                        case 2 -> // Service Besar
                            totalHarga = processServiceBesar(scanner, selectedServices, totalHarga);
                        default -> {
                            System.out.println("Pilihan tidak valid! Silakan pilih antara 1 dan 2.");
                            return;
                        }
                    }

                    // Ask the user if they want to continue or exit the selection
                    continueService = askContinueExit(scanner);
                }

                // Print out the receipt
                printReceipt(selectedServices, totalHarga);

                // Proceed to the payment process
                processPayment(scanner, totalHarga);

                // After payment, ask whether to continue to a new transaction or exit
                continueTransaction = askNewTransaction(scanner);
            }

            System.out.println("Terimakasih telah menggunakan layanan kami! Program selesai.");
        }
    }

    private static int processServiceKecil(Scanner scanner, StringBuilder selectedServices, int totalHarga) {
        boolean continueSelecting = true;

        while (continueSelecting) {
            System.out.println("\nPilih layanan untuk Service Kecil:");
            System.out.println("1. Ganti Oli (Rp 50.000)");
            System.out.println("2. Periksa Rem (Rp 30.000)");
            System.out.println("3. Cek Kondisi Ban (Rp 150.000)");
            System.out.println("4. Cuci Motor (Rp 20.000)");
            System.out.println("5. Selesai memilih layanan");
            System.out.print("Masukkan nomor pilihan layanan (1-5): ");
            int serviceChoice = scanner.nextInt();

            switch (serviceChoice) {
                case 1 -> {
                    selectedServices.append("Ganti Oli, ");
                    totalHarga += HARGA_GANTI_OLI;
                }
                case 2 -> {
                    selectedServices.append("Periksa Rem, ");
                    totalHarga += HARGA_CEK_REM;
                }
                case 3 -> {
                    selectedServices.append("Cek Kondisi Ban, ");
                    totalHarga += HARGA_GANTI_BAN;
                }
                case 4 -> {
                    selectedServices.append("Cuci Motor, ");
                    totalHarga += HARGA_CEK_RANTAI;
                }
                case 5 -> {
                    System.out.println("Anda selesai memilih layanan Service Kecil.");
                    continueSelecting = false;
                }
                default -> System.out.println("Pilihan tidak valid! Silakan pilih antara 1 hingga 5.");
            }

            if (continueSelecting) {
                continueSelecting = askToContinue(scanner);
            }
        }
        return totalHarga;
    }

    private static int processServiceBesar(Scanner scanner, StringBuilder selectedServices, int totalHarga) {
        boolean continueSelecting = true;

        while (continueSelecting) {
            System.out.println("\nPilih layanan untuk Service Besar:");
            System.out.println("1. Service Besar (Ganti Oli + Cek Kelistrikan + Periksa Mesin) (Rp 200.000)");
            System.out.println("2. Service Besar (Cek Kelistrikan + Ganti Oli + Periksa Rem) (Rp 175.000)");
            System.out.println("3. Selesai memilih layanan");
            System.out.print("Masukkan nomor pilihan layanan (1-3): ");
            int serviceChoice = scanner.nextInt();

            switch (serviceChoice) {
                case 1 -> {
                    selectedServices.append("Service Besar (Ganti Oli + Cek Kelistrikan + Periksa Mesin), ");
                    totalHarga += 200000;
                }
                case 2 -> {
                    selectedServices.append("Service Besar (Cek Kelistrikan + Ganti Oli + Periksa Rem), ");
                    totalHarga += 175000;
                }
                case 3 -> {
                    System.out.println("Anda selesai memilih layanan Service Besar.");
                    continueSelecting = false;
                }
                default -> System.out.println("Pilihan tidak valid! Silakan pilih antara 1 hingga 3.");
            }

            if (continueSelecting) {
                continueSelecting = askToContinue(scanner);
            }
        }
        return totalHarga;
    }

    // Function to ask user if they want to continue selecting services or close
    private static boolean askToContinue(Scanner scanner) {
        System.out.print("Apakah Anda ingin menambahkan layanan lainnya? (y/n): ");
        String addAnother = scanner.next();
        if (addAnother.equalsIgnoreCase("n")) {
            System.out.println("Anda selesai memilih layanan.");
            return false;
        }
        return true;
    }

    // Ask the user whether to continue adding services or exit
    private static boolean askContinueExit(Scanner scanner) {
        System.out.print("\nApakah Anda ingin menambahkan layanan lainnya? (y/n): ");
        String continueChoice = scanner.next();
        return continueChoice.equalsIgnoreCase("y");
    }

    private static void printReceipt(StringBuilder selectedServices, int totalHarga) {
        // Remove last comma and space if any
        if (selectedServices.length() > 0) {
            selectedServices.setLength(selectedServices.length() - 2);
        }

        System.out.println("\n==================== STRUK LAYANAN ====================");
        System.out.println("Layanan yang dipilih: " + selectedServices);
        System.out.println("Total Harga layanan: Rp " + totalHarga);
        System.out.println("=========================================================");
    }

    private static void processPayment(Scanner scanner, int totalHarga) {
        System.out.println("\nPilih metode pembayaran:");
        System.out.println("1. Tunai");
        System.out.println("2. Transfer Bank");
        System.out.println("3. E-wallet");
        System.out.print("Masukkan nomor pilihan metode pembayaran (1-3): ");
        int paymentMethod = scanner.nextInt();

        switch (paymentMethod) {
            case 1 -> {
                System.out.println("\nAnda memilih pembayaran dengan **Tunai**.");
                System.out.print("Masukkan jumlah uang yang dibayar: Rp ");
                int cashPaid = scanner.nextInt();
                if (cashPaid < totalHarga) {
                    System.out.println("Uang yang Anda bayar kurang. Silakan bayar dengan jumlah yang tepat.");
                } else {
                    int change = cashPaid - totalHarga;
                    System.out.println("Pembayaran berhasil! Kembalian: Rp " + change);
                }
            }
            case 2 -> {
                System.out.println("\nAnda memilih pembayaran dengan **Transfer Bank**.");
                System.out.println("Silakan transfer sejumlah Rp " + totalHarga + " ke rekening berikut: ");
                System.out.println("Rekening Bank: 123-456-789 (A/N: Robby Jansen)");
            }
            case 3 -> {
                System.out.println("\nAnda memilih pembayaran dengan **E-wallet**.");
                System.out.println("Silakan bayar menggunakan aplikasi E-wallet kami (083150406701) DANA.");
            }
            default -> System.out.println("Pilihan pembayaran tidak valid! Silakan pilih antara 1 hingga 3.");
        }
    }

    // Function to ask if the user wants to continue to a new transaction
    private static boolean askNewTransaction(Scanner scanner) {
        System.out.print("\nApakah Anda ingin melakukan transaksi berikutnya? (y/n): ");
        String continueChoice = scanner.next();
        return continueChoice.equalsIgnoreCase("y");
    }
}

