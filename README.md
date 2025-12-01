# Lab10Web.

    Nama: Burhan Isnain Nur Huda  
    NIM: 312410226  
    Kelas: TI.24.A.2  
    Mata Kuliah: Pemrograman Web 1
    Laporan Praktikum 10: PHP OOP
    
Informasi Praktikum

Praktikum: 10 - PHP Object-Oriented Programming

Tujuan: Memahami konsep OOP, Class, Object, dan membuat program OOP sederhana

Struktur Repository
Lab10Web/
├── README.md
├── index.php
├── Mobil.php
├── FormBuilder.php
├── Database.php
├── config.php
└── screenshots/
    ├── folder-struktur.png
    ├── database-connection.png
    ├── mobil-demo.png
    ├── form-demo.png
    └── crud-demo.png

#### Langkah-langkah Praktikum

Langkah 1: Setup Folder dan File
Buat folder ``lab10_php_oop`` di dalam ``htdocs`` dan buat file-file berikut:

Screenshot:
<img width="440" height="476" alt="image" src="https://github.com/user-attachments/assets/3b1c2e69-28ab-439d-b95f-325c7add4845" />


### Langkah 2: Class Mobil

File: `Mobil.php`

    <?php
    class Mobil {
    private $merk;
    private $warna;
    private $harga;
    
    // Constructor
    public function __construct($merk = "Toyota", $warna = "Hitam", $harga = 0) {
        $this->merk = $merk;
        $this->warna = $warna;
        $this->harga = $harga;
    }
    
    // Getter methods
    public function getMerk() {
        return $this->merk;
    }
    
    public function getWarna() {
        return $this->warna;
    }
    
    public function getHarga() {
        return "Rp " . number_format($this->harga, 0, ',', '.');
    }
    
    // Setter methods
    public function setWarna($warna) {
        $this->warna = $warna;
    }
    
    public function setHarga($harga) {
        $this->harga = $harga;
    }
    
    // Method untuk menampilkan info
    public function tampilInfo() {
        echo "Mobil: {$this->merk}<br>";
        echo "Warna: {$this->warna}<br>";
        echo "Harga: {$this->getHarga()}<br><br>";
    }
    }

    // Penggunaan class
    $mobil1 = new Mobil("Honda", "Merah", 250000000);
    $mobil1->tampilInfo();

    $mobil2 = new Mobil();
    $mobil2->setWarna("Biru");
    $mobil2->setHarga(300000000);
    $mobil2->tampilInfo();
    ?>

Konsep OOP yang diterapkan:

Class: Template untuk membuat object

Object: Instance dari class (`$mobil1`, `$mobil2`)

Property: `$merk`, `$warna`, `$harga`

Method: `tampilInfo()`, `setWarna()`, `getHarga()`

Constructor: `__construct()` untuk inisialisasi

Encapsulation: Property `private`, method `public`

Screenshot:
<img width="1900" height="957" alt="image" src="https://github.com/user-attachments/assets/62f88668-95c2-46f9-b77b-db50672b1d11" />

### Langkah 3: Class FormBuilder

File: `FormBuilder.php`

    <?php
    class FormBuilder {
    private $fields = [];
    
    public function addField($name, $label) {
        $this->fields[] = [
            'name' => $name,
            'label' => $label
        ];
        return $this; // Fluent interface
    }
    
    public function render() {
        echo '<form method="POST" style="max-width: 400px; margin: 20px auto; padding: 20px; border: 1px solid #ccc;">';
        
        foreach ($this->fields as $field) {
            echo '<div style="margin-bottom: 15px;">';
            echo '<label>' . $field['label'] . '</label><br>';
            echo '<input type="text" name="' . $field['name'] . '" style="width: 100%; padding: 8px;">';
            echo '</div>';
        }
        
        echo '<button type="submit" style="background: blue; color: white; padding: 10px 20px; border: none;">Submit</button>';
        echo '</form>';
    }
    }

    // Penggunaan
    $form = new FormBuilder();
     $form->addField("nama", "Nama Lengkap")
     ->addField("email", "Email")
     ->addField("nim", "NIM")
     ->render();
    ?>

Konsep OOP yang diterapkan:

Method Chaining: addField()->addField()->render()

Array Property: Menyimpan field dalam array

Dynamic Rendering: Form dibuat berdasarkan data array

Screenshot:
<img width="1905" height="953" alt="image" src="https://github.com/user-attachments/assets/e17c596c-12b5-49e8-8ef7-7db6902e7ceb" />
