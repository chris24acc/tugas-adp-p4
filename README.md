#include <iostream>
using namespace std;

int main() {
    cout << "===Selamat Datang di toko alat musik Christopher===" << endl;
    int total = 0;
    int jumlah_piano = 0, jumlah_biola = 0, jumlah_flute = 0;

    do {
        cout << "========= MENU TOKO=======================" << endl;
        cout << "| NO | NAMA ALAT MUSIK |      HARGA      |" << endl;
        cout << "-----------------------------------------" << endl;
        cout << "| 1. | Grand Piano     | Rp125.000.000   |" << endl;
        cout << "| 2. | Biola           | Rp25.000.000    |" << endl;
        cout << "| 3. | Flute           | Rp15.000.000    |" << endl;
        cout << "=========================================" << endl;

        cout << "\nSyarat diskon:" << endl;
        cout << "- Diskon 25% untuk pembelian 2 atau lebih Grand Piano." << endl;
        cout << "- Diskon 20% untuk pembelian 5 atau lebih Biola." << endl;
        cout << "- Diskon 15% untuk pembelian 5 atau lebih Flute." << endl;
        cout << "- Diskon tambahan 5% untuk total belanja minimal Rp500.000.000" << endl;

        int KODE, jumlah;
        cout << "Masukkan Nomor Barang: ";
        cin >> KODE;

        int harga = 0;
        if (KODE == 1) {
            harga = 125000000;
            cout << "Masukkan jumlah Grand Piano: ";
            cin >> jumlah;
            jumlah_piano += jumlah;
        } else if (KODE == 2) {
            harga = 25000000;
            cout << "Masukkan jumlah Biola: ";
            cin >> jumlah;
            jumlah_biola += jumlah;
        } else if (KODE == 3) {
            harga = 15000000;
            cout << "Masukkan jumlah Flute: ";
            cin >> jumlah;
            jumlah_flute += jumlah;
        } else {
            cout << "Barang tidak terdaftar" << endl;
            continue;
        }

        total += harga * jumlah;

        char lagi;
        cout << "Beli barang lain?\nTekan (Y/N): ";
        cin >> lagi;
        if (toupper(lagi) == 'N') {
            break;
        }
    } while (true);


    bool diskon_piano = false, diskon_biola = false, diskon_flute = false;
    bool diskon_tambahan = false;


    if (jumlah_piano >= 2) {
        total -= jumlah_piano * 125000000 * 0.25;
        diskon_piano = true;
    }
    if (jumlah_biola >= 5) {
        total -= jumlah_biola * 25000000 * 0.2;
        diskon_biola = true;
    }
    if (jumlah_flute >= 5) {
        total -= jumlah_flute * 15000000 * 0.15;
        diskon_flute = true;
    }


    if (total >= 500000000) {
        total -= total * 0.05;
        diskon_tambahan = true;
    }

    cout << "\nTotal Bayar: Rp " << total << endl;


    if (diskon_piano) {
        cout << "Anda mendapat diskon 25% karena membeli 2 atau lebih Grand Piano." << endl;
    }
    if (diskon_biola) {
        cout << "Anda mendapat diskon 20% karena membeli 5 atau lebih Biola." << endl;
    }
    if (diskon_flute) {
        cout << "Anda mendapat diskon 15% karena membeli 5 atau lebih Flute." << endl;
    }
    if (diskon_tambahan) {
        cout << "Anda mendapat diskon tambahan sebesar 5% karena total belanja mencapai Rp500.000.000." << endl;
    }

    int bayar;
    cout << "\nMasukkan jumlah uang yang dibayarkan: Rp ";
    cin >> bayar;

    if (bayar > total) {
        cout << "Sisa uang kembali: Rp " << bayar - total << endl;
    } else if (bayar == total) {
        cout << "Uang Anda Pas Ya!" << endl;
    } else {
        cout << "Uang Anda Kurang : Rp " << total - bayar << endl;
    }
    cout << "Terima Kasih ^-^";

    return 0;
}
