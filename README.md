# praktikum6
# soal 1
![Cuplikan layar 2024-11-07 070918](https://github.com/user-attachments/assets/09bdf4e1-9c2b-429c-aa5d-d382fc6abd76)
# soal 2
![Cuplikan layar 2024-11-07 070940](https://github.com/user-attachments/assets/dc6a3d46-f797-429c-9136-7311fc1ee39b)

# jawaban 1
![code pertemuan 7](https://github.com/user-attachments/assets/0dcf0a68-bc56-43f8-b53d-d23e669ae3fe)

     class Pegawai {
    private String nama;
    private double gajiPokok;

    public Pegawai(String nama, double gajiPokok) {
        this.nama = nama;
        this.gajiPokok = gajiPokok;
    }

    public Pegawai(String nama) {
        this.nama = nama;
        this.gajiPokok = 0; 
    }

    public void setNama(String nama) {
        this.nama = nama;
    }

    public String getNama() {
        return nama;
    }

    public void setGajiPokok(double gajiPokok) {
        this.gajiPokok = gajiPokok;
    }

    public double getGajiPokok() {
        return gajiPokok;
    }

    public void cetakInfo() {
        System.out.printf("Nama: %s, Gaji Pokok: %.0f%n", nama, gajiPokok);
    }
    }

    @SuppressWarnings("unused")
    class Manager extends Pegawai {
           private double tunjangan;

    public Manager(String nama, double gajiPokok, double tunjangan) {
        super(nama, gajiPokok);
        this.tunjangan = tunjangan;
    }

    public Manager(String nama, double gajiPokok) {
        super(nama, gajiPokok);
        this.tunjangan = 0; 
    }

    public void setTunjangan(double tunjangan) {
        this.tunjangan = tunjangan;
    }

    public double getTunjangan() {
        return tunjangan;
    }

    @Override
    public void cetakInfo() {
        super.cetakInfo();
        System.out.printf("Tunjangan: %.0f%n", tunjangan);
    }
    }

    class Programmer extends Pegawai {
    private double bonus;

    public Programmer(String nama, double gajiPokok, double bonus) {
        super(nama, gajiPokok);
        this.bonus = bonus;
    }

    public Programmer(String nama, double gajiPokok) {
        super(nama, gajiPokok);
        this.bonus = 0; 
    }

    public Programmer(String nama) {
        super(nama);
        this.bonus = 0; 
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }

    public double getBonus() {
        return bonus;
    }

    @Override
    public void cetakInfo() {
        super.cetakInfo();
        System.out.printf("Bonus: %.0f%n", bonus);
    }
    }

    public class main {
    public static void main(String[] args) {
        Programmer programmer1 = new Programmer("Andi Herlambang");
        Programmer programmer2 = new Programmer("Riko", 6000000);
        Programmer programmer3 = new Programmer("Dina", 5000000, 3000000);

        System.out.println("Info Programmer 1:");
        programmer1.cetakInfo();
        System.out.println("\nInfo Programmer 2:");
        programmer2.cetakInfo();
        System.out.println("\nInfo Programmer 3:");
        programmer3.cetakInfo();
    }
    }
# output
![Cuplikan layar 2024-11-07 070618](https://github.com/user-attachments/assets/20caf10a-34b5-49c9-bef3-e8982a9d7325)

# jawaban 2
![code pertemuan 7 ke 2](https://github.com/user-attachments/assets/c2abe485-ffe7-45cd-b057-0fabe9912f6e)

    import java.text.DecimalFormat;
    import java.text.SimpleDateFormat;
    import java.util.ArrayList;
    import java.util.Calendar;
    import java.util.Date;
    import java.util.List;

    class Produk {
    protected String namaProduk;
    protected double harga;
    protected int jumlahStok;

    public Produk(String namaProduk, double harga, int jumlahStok) {
        this.namaProduk = namaProduk;
        this.harga = harga;
        this.jumlahStok = jumlahStok;
    }

    public void displayInfo() {
        DecimalFormat df = new DecimalFormat("#.##");
        System.out.println("Nama Produk: " + namaProduk);
        System.out.println("Harga: " + df.format(harga));
        System.out.println("Jumlah Stok: " + jumlahStok);
    }
    }

    class Elektronik extends Produk {
    @SuppressWarnings("FieldMayBeFinal")
    private int garansi;

    public Elektronik(String namaProduk, double harga, int jumlahStok, int garansi) {
        super(namaProduk, harga, jumlahStok);
        this.garansi = garansi;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Garansi: " + garansi + " tahun");
    }
    }
  
    class Pakaian extends Produk {
    @SuppressWarnings("FieldMayBeFinal")
    private String ukuran;
    @SuppressWarnings("FieldMayBeFinal")
    private String warna;

    public Pakaian(String namaProduk, double harga, int jumlahStok, String ukuran, String warna) {
        super(namaProduk, harga, jumlahStok);
        this.ukuran = ukuran;
        this.warna = warna;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        System.out.println("Ukuran: " + ukuran);
        System.out.println("Warna: " + warna);
    }
    }

    class Makanan extends Produk {
    private Date tanggalKadaluarsa;

    public Makanan(String namaProduk, double harga, int jumlahStok, Date tanggalKadaluarsa) {
        super(namaProduk, harga, jumlahStok);
        this.tanggalKadaluarsa = tanggalKadaluarsa;
    }

    public void setTanggalKadaluarsa(Date tanggalKadaluarsa) {
        this.tanggalKadaluarsa = tanggalKadaluarsa;
    }

    @Override
    public void displayInfo() {
        super.displayInfo();
        SimpleDateFormat dateFormat = new SimpleDateFormat("dd-MM-yyyy");
        System.out.println("Tanggal Kadaluarsa: " + dateFormat.format(tanggalKadaluarsa));
    }
    }

    class KeranjangBelanja {
    @SuppressWarnings("FieldMayBeFinal")
    private List<Produk> daftarProduk;
    private List<Integer> jumlahProduk;

    public KeranjangBelanja() {
        daftarProduk = new ArrayList<>();
        jumlahProduk = new ArrayList<>();
    }

    public void tambahProduk(Produk p, int jumlah) {
        if (p.jumlahStok >= jumlah) {
            daftarProduk.add(p);
            jumlahProduk.add(jumlah);
            p.jumlahStok -= jumlah;
            System.out.println(jumlah + " " + p.namaProduk + " ditambahkan ke keranjang.");
        } else {
            System.out.println("Stok tidak mencukupi untuk " + p.namaProduk);
        }
    }

    public double hitungTotalBelanja() {
        double total = 0;
        for (int i = 0; i < daftarProduk.size(); i++) {
            total += daftarProduk.get(i).harga * jumlahProduk.get(i);
        }
        return total;
    }

    public void displayKeranjang() {
        DecimalFormat df = new DecimalFormat("#.##");
        System.out.println("Isi Keranjang Belanja:");
        for (int i = 0; i < daftarProduk.size(); i++) {
            Produk p = daftarProduk.get(i);
            int jumlah = jumlahProduk.get(i);
            p.displayInfo();
            System.out.println("Jumlah: " + jumlah);
            System.out.println("Subtotal: " + df.format(p.harga * jumlah));
            System.out.println();
        }
        System.out.println("Total Harga Semua Produk di Keranjang: " + df.format(hitungTotalBelanja()));
    }

    public List<Integer> getJumlahProduk() {
        return jumlahProduk;
    }

    public void setJumlahProduk(List<Integer> jumlahProduk) {
        this.jumlahProduk = jumlahProduk;
    }
    }

    public class ShopingCart {
    public static void main(String[] args) {
        Elektronik laptop = new Elektronik("Laptop", 8000000, 10, 2);
        Pakaian sepatu = new Pakaian("Sepatu", 100000, 50, "L", "Hitam");

        Calendar cal = Calendar.getInstance();
        cal.set(2024, Calendar.NOVEMBER, 7); 
        Date tanggalKadaluarsa = cal.getTime();
        
        Makanan roti = new Makanan("Roti", 50000, 30, tanggalKadaluarsa);

        KeranjangBelanja keranjang = new KeranjangBelanja();

        keranjang.tambahProduk(laptop, 1);
        keranjang.tambahProduk(sepatu, 3);
        keranjang.tambahProduk(roti, 5);

        keranjang.displayKeranjang();
    }
    }

![Cuplikan layar 2024-11-07 070714](https://github.com/user-attachments/assets/7517c9f7-837d-4dc4-bad8-5c2b26bbca95)
