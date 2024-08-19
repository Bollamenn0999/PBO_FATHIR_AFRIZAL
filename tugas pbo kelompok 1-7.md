~~~dart
void main() {
  // Data awal
  double hargaRumah = 500000000; // Harga rumah
  int durasiTahun = 20; // Durasi cicilan dalam tahun
  double bungaPertahun = 0.06; // Bunga per tahun
  int jumlahCicilan = durasiTahun * 12; // Jumlah cicilan (bulan)

  // Fungsi untuk menghitung cicilan bulanan
  double hitungCicilanBulanan(double harga, int durasiBulan, double bunga) {
    double bungaBulanan = bunga / 12;
    return (harga * bungaBulanan) / (1 - (1 / (1 + bungaBulanan)).pow(durasiBulan));
  }

  // Fungsi untuk menampilkan rincian cicilan
  void tampilkanRincianCicilan(List<double> cicilanList) {
    for (int i = 0; i < cicilanList.length; i++) {
      print('Bulan ${i + 1}: Rp ${cicilanList[i].toStringAsFixed(2)}');
    }
  }

  // Closure untuk menghitung total pembayaran
  var hitungTotalPembayaran = (List<double> cicilanList) {
    double total = 0;
    for (double cicilan in cicilanList) {
      total += cicilan;
    }
    return total;
  };

  // Perhitungan cicilan bulanan
  double cicilanBulanan = hitungCicilanBulanan(hargaRumah, jumlahCicilan, bungaPertahun);

  // List untuk menyimpan nilai cicilan setiap bulan
  List<double> cicilanList = [];

  // Loop untuk mengisi list dengan nilai cicilan
  for (int i = 0; i < jumlahCicilan; i++) {
    cicilanList.add(cicilanBulanan);
  }

  // Tampilkan rincian cicilan
  tampilkanRincianCicilan(cicilanList);

  // Hitung dan tampilkan total pembayaran
  double totalPembayaran = hitungTotalPembayaran(cicilanList);
  print('Total pembayaran selama $durasiTahun tahun: Rp ${totalPembayaran.toStringAsFixed(2)}');
}
~~~