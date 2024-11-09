# 📖 Pertemuan Keduabelas - Aplikasi CRUD JPA (Java Persistence APl) 
## 📂 Topik Utama 
Langkah - langkah CRUD dengan menggunakan Persistence

## 📜 Daftar Isi 
- [Koneksi Dtabase dengan JPA](https://github.com/fauziaeka/TugasPBO_TM12/blob/main/persistence.xml)
- [Konfigurasi Persistence Unit](https://github.com/fauziaeka/TugasPBO_TM12/blob/main/Matakuliah.java)
- [Implementasi CRUD](https://github.com/fauziaeka/TugasPBO_TM12/blob/main/FrameMataKuliah.java)

## 📋 Langkah - Langkah 
1. Membuat projek baru dengan nama “PBO_TM12” dan uncheklist pada create main class

   ![image](https://github.com/user-attachments/assets/dd14f29e-2518-49c8-afb9-d84a4bd2b0a0)

2.	Membuat package baru dengan nama “pbo_tm12”

   ![image](https://github.com/user-attachments/assets/389e0150-7f9d-4e85-b294-287ec795949e)

3.	Buat persistence dengan cara klik kanan pada package, klik new kemudian pilih Entity Classes from Database

   ![image](https://github.com/user-attachments/assets/d9c5d466-5966-4970-ae27-5e500cfa9967)

4.	Pilih database yang akan digunakan

   ![image](https://github.com/user-attachments/assets/6ea2ce5c-55d0-4ab1-8725-39a5584eb415)

5.	Masukkan password postgresql

   ![image](https://github.com/user-attachments/assets/0fc946b4-562f-4031-88a5-0aff06c379f2)

6.	Pindahkan table pada sebelah kiri ke sebelah kanan dengan cara klik Add All >>

   ![image](https://github.com/user-attachments/assets/58057d97-6047-4d1b-bb1c-34d9ad223cb5)

   ![image](https://github.com/user-attachments/assets/a6938994-f06c-4941-a03b-90ab6460ef92)

7.	Setelah tampilan seperti ini, klik next

   ![image](https://github.com/user-attachments/assets/ab33264c-307a-404c-abad-c5c0a091060d)

8. Setelah tampilan seperti ini, klik finish. Maka persistence telah berhasil dibuat

   ![image](https://github.com/user-attachments/assets/d0265223-c6a9-4c9b-b140-264fb74e9100)

9.	Berikut merupakan library yang akan muncul saat berhasil membuat persistence

    ![image](https://github.com/user-attachments/assets/3791b97b-ffcc-44ba-9e16-8f90742d4bf4)

10.	Masukkan add library untuk menambahkan sambungan postgreSQL JDBC Driver

    ![image](https://github.com/user-attachments/assets/006be752-df94-499b-92e7-69e936b91c80)

    ![image](https://github.com/user-attachments/assets/7b0d4e87-bf14-4e75-ad0d-cf1a7ad08650)

11.	Masukkan library untuk menambahkan Jasper Report yang berfungsi untuk mencetak data

    ![image](https://github.com/user-attachments/assets/4e2c364f-a1e1-4163-80c4-439104692b2d)

    ![image](https://github.com/user-attachments/assets/9aabffc6-93c1-4650-88c3-6247803202d7)

    ![image](https://github.com/user-attachments/assets/7301af31-6606-4559-bb13-46da80442251)

12.	Berikut tampilan persistence yang berhasil dibuat

    ![image](https://github.com/user-attachments/assets/88d0e0af-f444-4d87-aec7-eb8138a38c32)

13.	Berikut merupakan source code yang terbentuk

```
package pbo_tm12;

import java.io.Serializable;
import javax.persistence.Basic;
import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.NamedQueries;
import javax.persistence.NamedQuery;
import javax.persistence.Table;
import javax.xml.bind.annotation.XmlRootElement;

/**
 *
 * @author win 10
 */
@Entity
@Table(name = "matakuliah")
@XmlRootElement
@NamedQueries({
    @NamedQuery(name = "Matakuliah.findAll", query = "SELECT m FROM Matakuliah m"),
    @NamedQuery(name = "Matakuliah.findByKodemk", query = "SELECT m FROM Matakuliah m WHERE m.kodemk = :kodemk"),
    @NamedQuery(name = "Matakuliah.findBySks", query = "SELECT m FROM Matakuliah m WHERE m.sks = :sks"),
    @NamedQuery(name = "Matakuliah.findByNamamk", query = "SELECT m FROM Matakuliah m WHERE m.namamk = :namamk"),
    @NamedQuery(name = "Matakuliah.findBySemesterajar", query = "SELECT m FROM Matakuliah m WHERE m.semesterajar = :semesterajar")})
public class Matakuliah implements Serializable {

    private static final long serialVersionUID = 1L;
    @Id
    @Basic(optional = false)
    @Column(name = "kodemk")
    private String kodemk;
    @Basic(optional = false)
    @Column(name = "sks")
    private int sks;
    @Basic(optional = false)
    @Column(name = "namamk")
    private String namamk;
    @Basic(optional = false)
    @Column(name = "semesterajar")
    private int semesterajar;

    public Matakuliah() {
    }

    public Matakuliah(String kodemk) {
        this.kodemk = kodemk;
    }

    public Matakuliah(String kodemk, int sks, String namamk, int semesterajar) {
        this.kodemk = kodemk;
        this.sks = sks;
        this.namamk = namamk;
        this.semesterajar = semesterajar;
    }

    public String getKodemk() {
        return kodemk;
    }

    public void setKodemk(String kodemk) {
        this.kodemk = kodemk;
    }

    public int getSks() {
        return sks;
    }

    public void setSks(int sks) {
        this.sks = sks;
    }

    public String getNamamk() {
        return namamk;
    }

    public void setNamamk(String namamk) {
        this.namamk = namamk;
    }

    public int getSemesterajar() {
        return semesterajar;
    }

    public void setSemesterajar(int semesterajar) {
        this.semesterajar = semesterajar;
    }

    @Override
    public int hashCode() {
        int hash = 0;
        hash += (kodemk != null ? kodemk.hashCode() : 0);
        return hash;
    }

    @Override
    public boolean equals(Object object) {
        // TODO: Warning - this method won't work in the case the id fields are not set
        if (!(object instanceof Matakuliah)) {
            return false;
        }
        Matakuliah other = (Matakuliah) object;
        if ((this.kodemk == null && other.kodemk != null) || (this.kodemk != null && !this.kodemk.equals(other.kodemk))) {
            return false;
        }
        return true;
    }

    @Override
    public String toString() {
        return "pbo_tm12.Matakuliah[ kodemk=" + kodemk + " ]";
    }
    
}
```

 
 14.	Membuat kelas MataKuliahDB kemudian isi source codenya
```
package pbo_tm12;

import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.util.Vector;
import javax.swing.table.DefaultTableModel;
import javax.swing.table.TableModel;

public class MataKuliahDB {

    public static TableModel resultSetToTableModel(ResultSet rs) {
        try {
            ResultSetMetaData metaData = rs.getMetaData();
            int numberOfColumns = metaData.getColumnCount();
            Vector columnNames = new Vector();

            // Get the column names
            for (int column = 0; column < numberOfColumns; column++) {
                columnNames.addElement(metaData.getColumnLabel(column + 1));
            }

            // Get all rows.
            Vector rows = new Vector();

            while (rs.next()) {
                Vector newRow = new Vector();

                for (int i = 1; i <= numberOfColumns; i++) {
                    newRow.addElement(rs.getObject(i));
                }

                rows.addElement(newRow);
            }

            return new DefaultTableModel(rows, columnNames);
        } catch (Exception e) {
            e.printStackTrace();

            return null;
        }
    }
}
```

15.	Membuat file laporan
    
a.	Buat class baru untuk design reportnya dengan cara klik kanan pada package ‘pbo_tm12’ kemudian pilih ‘new’ dan pilih ‘report wizard

![image](https://github.com/user-attachments/assets/a1af8e11-c5f5-4066-a1f3-03281750600f)

b.	Pilih design layout

![image](https://github.com/user-attachments/assets/6e3049e9-24e7-4948-a92a-577be2a5f758)

c.	Sambungkan ke database yang telah disiapkan, klik next. Kemudian masukkan nama database, username, dan password lalu klik next

![image](https://github.com/user-attachments/assets/989ebf23-ab3c-47c6-bee9-adf737bdcc0f)

d.	Pilih query dan ketikkan secara manual ‘select * from matakuliah;’ atau bisa juga pilih design query jika memiliki banyak table 

![image](https://github.com/user-attachments/assets/89f7ce02-a07d-4e76-af0a-1bd8759ac3ca)

e.	Masukkan password database, klik OK

![image](https://github.com/user-attachments/assets/f4a03547-1e51-4c4e-a8af-de67b8c56e70)

f.	Atur Group by sesuai dengan tabel pada database, lalu pindahkan ke sebelah kanan dan klik next

![image](https://github.com/user-attachments/assets/e8ac2d8d-35fd-433c-b355-3fd3b14a3d2c)

![image](https://github.com/user-attachments/assets/562f81ce-61fe-4c06-ae5f-8c6fdb9cc12f)

g.	Setelah muncul seperti ini, klik next

![image](https://github.com/user-attachments/assets/9093d9e3-ee6f-414f-9a07-342f625e20dd)

h.	Jika muncul tampilan seperti ini, maka telah berhasil membuat report baru
 
![image](https://github.com/user-attachments/assets/0fb01a19-3d5c-4c60-a582-6fe843e6e471)

i.	Membuat design pada class Jasper Wizard 

![image](https://github.com/user-attachments/assets/a1eeeff9-7ca4-468d-b6f3-77f50d90a53c)

16.	Memasukkan data ke CSV

a.	Membuat data Mata Kuliah pada MS EXCEL yang terdiri dari 4 kolom yang berisi Kode Mata Kuliah, SKS, Nama Mata Kuliah dan Semester Ajar

![image](https://github.com/user-attachments/assets/34515c8f-554c-4f17-96c2-084b822a79fd)

b.	Simpan dalam format CSV (Comma Delimited)

![image](https://github.com/user-attachments/assets/05b7c239-cae2-4fc3-882d-bfe86ac5cebc)

17.	Membuat desain pada Jframe Form

![image](https://github.com/user-attachments/assets/9071e941-7c6f-4211-9247-dc4bc728cb7b)

18.	Mengisi source code dari Jframe Form agar program dapat berjalan 

a.	Mendeklarasikan import kelas-kelas yang diperlukan

```

package pbo_tm12;

import java.awt.HeadlessException;
import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.logging.Level;
import java.util.logging.Logger;
import javax.swing.JOptionPane;
import javax.swing.table.TableModel;
import javax.swing.table.DefaultTableModel;
import pbo_tm12.MataKuliahDB;
import net.sf.jasperreports.engine.JasperReport;
import net.sf.jasperreports.engine.*;
import net.sf.jasperreports.view.JasperViewer;
import net.sf.jasperreports.engine.util.JRLoader;
import java.sql.Connection;
import java.util.List;
import javax.persistence.EntityManager;
import javax.persistence.EntityManagerFactory;
import javax.persistence.EntityTransaction;
import javax.persistence.Persistence;
import javax.persistence.Query;
import javax.swing.JFileChooser;
import javax.swing.JScrollPane;
import javax.swing.filechooser.FileSystemView;
import net.sf.jasperreports.engine.JasperFillManager;
import net.sf.jasperreports.engine.JasperPrint;

/**
 *
 * @author win 10
 */
public class FrameMataKuliah extends javax.swing.JFrame {

    Connection conn;
    PreparedStatement pstmt;
    ResultSet rs;
    String driver = "org.postgresql.Driver";
    String koneksi = "jdbc:postgresql://localhost:5432/PBO_TM10";
    String user = "postgres";
    String password = "123456";
    private BufferedReader input = new BufferedReader(new InputStreamReader(System.in));

    /**
     * Creates new form FrameMataKuliah
     */
    private DefaultTableModel tbmk;

    public FrameMataKuliah() {
        initComponents();
        tampil();
    }
```

 
b.	Membuat method tampil yang digunakan untuk menampilkan data pada GUI

```
 public void tampil() {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_TM12PU");
        EntityManager em = emf.createEntityManager();

        try {
            Query query = em.createNamedQuery("Matakuliah.findAll");
            List<Matakuliah> hasil = query.getResultList();

            tbmk = new DefaultTableModel(new String[]{"Kode Mata Kuliah", "SKS", "Nama Mata Kuliah", "Semester Ajar"}, 0);

            for (Matakuliah data : hasil) {
                Object[] baris = new Object[4];
                baris[0] = data.getKodemk();
                baris[1] = data.getSks();
                baris[2] = data.getNamamk();
                baris[3] = data.getSemesterajar();
                tbmk.addRow(baris);
            }

            tblMataKuliah.setModel(tbmk);

        } catch (Exception e) {
            JOptionPane.showMessageDialog(this, "Terjadi kesalahan: " + e.getMessage());
        } finally {
            em.close();
        }
    }
```

c.	Mengisi code pada btnInsert yang berfungsi untuk menambahkan data. Button ini berfungsi untuk menambahkan data pada 'Data Mata Kuliah'. Sebagai pengguna, kita diminta untuk mengisi informasi mengenai kodeMK, sks, namaMK, semesterAjar. Setelah dimasukkan, kita bisa menekan button Insert. Jika berhasil, akan muncul pesan 'Data Berhasil disimpan'

```
private void btnInsertActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        String kodeMK = tfKodeMK.getText();
        String sks = tfSKS.getText();
        String namaMK = tfNamaMK.getText();
        String semesterAjar = tfSemesterAjar.getText();

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_TM12PU");
        EntityManager em = emf.createEntityManager();
        EntityTransaction transaction = em.getTransaction();

        try {
            transaction.begin();

            Matakuliah matakuliah = new Matakuliah();
            matakuliah.setKodemk(kodeMK);
            matakuliah.setSks(Integer.parseInt(sks));
            matakuliah.setNamamk(namaMK);
            matakuliah.setSemesterajar(Integer.parseInt(semesterAjar));

            em.persist(matakuliah);

            transaction.commit();

            JOptionPane.showMessageDialog(null, "Data berhasil disimpan");

        } catch (NumberFormatException e) {
            if (transaction.isActive()) {
                transaction.rollback();
            }
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan pada format angka: " + e.getMessage());
        } catch (HeadlessException e) {
            if (transaction.isActive()) {
                transaction.rollback();
            }
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + e.getMessage());
        } finally {
            em.close();
        }

        bersih();
        tampil();
    }                            
```

d.	Mengisi code pada btnUpdate yang berfungsi untuk memperbarui data. Pertama-tama masukkan kodeMK yang ingin diubah, kemudian masukkan informasi mengenai sks, namaMK, dan semesterAjar baru. Jika berhasil, sistem akan mencetak pemberitahuan bahwa 'Data berhasil diupdate'.

```
private void btnUpdateActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        String kodeMK, sks, namaMK, semesterAjar;

        if (tfKodeMK.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Kode Mata Kuliah harus diisi");
            return;
        }
        if (tfSKS.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "SKS Mata Kuliah harus diisi");
            return;
        }
        if (tfNamaMK.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Nama Mata Kuliah harus diisi");
            return;
        }
        if (tfSemesterAjar.getText().isEmpty()) {
            JOptionPane.showMessageDialog(null, "Semester Ajar harus diisi");
            return;
        }

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_TM12PU");
        EntityManager em = emf.createEntityManager();
        EntityTransaction transaction = em.getTransaction();

        try {
            transaction.begin();

            kodeMK = tfKodeMK.getText();
            sks = tfSKS.getText();
            namaMK = tfNamaMK.getText();
            semesterAjar = tfSemesterAjar.getText();

            Matakuliah matakuliah = em.find(Matakuliah.class, kodeMK);

            if (matakuliah != null) {
                matakuliah.setSks(Integer.parseInt(sks));
                matakuliah.setNamamk(namaMK);
                matakuliah.setSemesterajar(Integer.parseInt(semesterAjar));

                em.merge(matakuliah);
                transaction.commit();

                JOptionPane.showMessageDialog(null, "Data berhasil diupdate");
                bersih();
            } else {
                JOptionPane.showMessageDialog(null, "Data tidak ditemukan");
            }

        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(null, "Input tidak valid: " + ex.getMessage());
            if (transaction.isActive()) {
                transaction.rollback();
            }
        } catch (Exception ex) {
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + ex.getMessage());
            if (transaction.isActive()) {
                transaction.rollback();
            }
        } finally {
            em.close();
        }

        tampil();
    }                                         
```

e.	Mengisi code pada btnDelete yang berfungsi untuk menghapus data pada 'Data Mata Kuliah'. Pengguna bisa memasukkan data yang ingin dihapus atau bisa juga dengan mengeklik data yang ingin dihapus pada kolom list. Kemudian akan muncul pesan konfirmasi apakah pengguna ingin menghapus data atau tidak. Jika 'iya' data otomatis akan dihapus dan jika 'tidak' maka data akan batal dihapus.

```
    private void btnDeleteActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        String kodeMK = tfKodeMK.getText();

        if (kodeMK.isEmpty()) {
            JOptionPane.showMessageDialog(null, "KodeMK tidak boleh kosong!", "Error", JOptionPane.ERROR_MESSAGE);
            return;
        }

        EntityManagerFactory emf = Persistence.createEntityManagerFactory("PBO_TM12PU");
        EntityManager em = emf.createEntityManager();
        EntityTransaction transaction = em.getTransaction();

        try {
            int jawab = JOptionPane.showConfirmDialog(null, "Apakah Anda yakin ingin menghapus MataKuliah dengan KodeMK: " + kodeMK + "?", "Konfirmasi Penghapusan", JOptionPane.YES_NO_OPTION);

            if (jawab == JOptionPane.YES_OPTION) {
                transaction.begin();

                Matakuliah matakuliah = em.find(Matakuliah.class, kodeMK);

                if (matakuliah != null) {
                    em.remove(matakuliah);
                    transaction.commit();
                    JOptionPane.showMessageDialog(null, "Data berhasil dihapus");
                } else {
                    JOptionPane.showMessageDialog(null, "Data tidak ditemukan untuk KodeMK: " + kodeMK);
                }
            } else {
                JOptionPane.showMessageDialog(this, "Penghapusan dibatalkan");
            }

        } catch (Exception ex) {
            if (transaction.isActive()) {
                transaction.rollback();
            }
            JOptionPane.showMessageDialog(null, "Terjadi kesalahan: " + ex.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        } finally {
            em.close();
        }

        tampil();
    }  
```

f.	Mengisi code pada btnExit yang berfungsi untuk keluar dari halaman yang menampilkan GUI dengan kembali ke halaman awal. 

```
 private void btnExitActionPerformed(java.awt.event.ActionEvent evt) {                                        
        // TODO add your handling code here:
        System.exit(0);
    }                                       
```

g.	Mengisi code pada program tblMataKuliahMouseClicked yang berfungsi untuk menampilkan data dalam bentuk tabel selain itu, pengguna juga dapat mengedit data tersebut. 

```
private void tblMataKuliahMouseClicked(java.awt.event.MouseEvent evt) {                                           
        // TODO add your handling code here:
        int row = tblMataKuliah.getSelectedRow();
        tfKodeMK.setText(tblMataKuliah.getValueAt(row, 0).toString());
        tfSKS.setText(tblMataKuliah.getValueAt(row, 1).toString());
        tfNamaMK.setText(tblMataKuliah.getValueAt(row, 2).toString());
        tfSemesterAjar.setText(tblMataKuliah.getValueAt(row, 3).toString());
        tampil();
    }        
```

h.	Mengisi code pada btnCetak yang berfungsi untuk mencetak file yang bisa disimpan ke dalam bentuk pdf 

```
private void btnCetakActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        try {
            if (conn == null || conn.isClosed()) {
                conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/PBO_TM10", "postgres", "123456");
            }

            String path = "src/pbo_tm12/MataKuliah.jasper";
            JasperReport report = (JasperReport) JRLoader.loadObjectFromFile(path);

            if (conn != null) {
                JasperPrint jprint = JasperFillManager.fillReport(report, null, conn);
                JasperViewer jviewer = new JasperViewer(jprint, false);
                jviewer.setDefaultCloseOperation(JasperViewer.DISPOSE_ON_CLOSE);
                jviewer.setVisible(true);
            } else {
                JOptionPane.showMessageDialog(null, "Koneksi database tidak tersedia.");
            }
        } catch (SQLException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Koneksi database gagal: " + e.getMessage());
        } catch (JRException e) {
            e.printStackTrace();
            JOptionPane.showMessageDialog(null, "Gagal mencetak laporan: " + e.getMessage());
        }
        tampil();
    }              
```

i.	Mengisi code btnUpload yang berfungsi untuk mengupload file CSV ke dalam program 

```
private void btnUploadActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
        JFileChooser jfc = new JFileChooser(FileSystemView.getFileSystemView().getHomeDirectory());
        int returnValue = jfc.showOpenDialog(null);
        if (returnValue == JFileChooser.APPROVE_OPTION) {
            File filePilihan = jfc.getSelectedFile();
            System.out.println("File yang dipilih : " + filePilihan.getAbsolutePath());

            EntityManagerFactory emf = null;
            EntityManager em = null;
            EntityTransaction transaction = null;
            BufferedReader br = null;

            try {
                emf = Persistence.createEntityManagerFactory("PBO_TM12PU");
                em = emf.createEntityManager();
                transaction = em.getTransaction();
                br = new BufferedReader(new FileReader(filePilihan));
                String baris;
                String pemisah = ";";

                while ((baris = br.readLine()) != null) {
                    String[] matakuliah = baris.split(pemisah);
   
                    if (matakuliah.length >= 4) {
                        String kodeMK = matakuliah[0];
                        String sks = matakuliah[1];
                        String namaMK = matakuliah[2];
                        String semesterAjar = matakuliah[3];

                        if (!kodeMK.isEmpty() && !sks.isEmpty() && !namaMK.isEmpty() && !semesterAjar.isEmpty()) {
                            try {
                                transaction.begin();

                                Matakuliah mk = new Matakuliah();
                                mk.setKodemk(kodeMK);
                                mk.setSks(Integer.parseInt(sks));
                                mk.setNamamk(namaMK);
                                mk.setSemesterajar(Integer.parseInt(semesterAjar));

                                em.persist(mk);

                                transaction.commit();
                                JOptionPane.showMessageDialog(null, "Input Data Berhasil!");
                            } catch (Exception e) {
                                if (transaction.isActive()) {
                                    transaction.rollback();
                                }
                                JOptionPane.showMessageDialog(null, "Input Data Gagal: " + e.getMessage());
                            }
                        }
                    } else {
                        System.out.println("Baris tidak memiliki cukup kolom: " + baris);
                    }
                }
            } catch (FileNotFoundException ex) {
                Logger.getLogger(MataKuliahDB.class.getName()).log(Level.SEVERE, null, ex);
            } catch (IOException ex) {
                Logger.getLogger(MataKuliahDB.class.getName()).log(Level.SEVERE, null, ex);
            } finally {
                // Pastikan EntityManager ditutup dengan aman
                try {
                    if (br != null) {
                        br.close();
                    }
                    if (em != null) {
                        em.close();
                    }
                    if (emf != null) {
                        emf.close();
                    }
                } catch (IOException e) {
                    JOptionPane.showMessageDialog(null, "Gagal menutup file: " + e.getMessage());
                } catch (Exception e) {
                    JOptionPane.showMessageDialog(null, "Terjadi kesalahan saat menutup EntityManager: " + e.getMessage());
                }
            }
        }
        tampil();
    }                                  
```

j.	Mengisi code pada program bersih() yang berfungsi untuk memastikan bahwa setelah data dimasukkan atau operasi selesai, semua input dari pengguna direset untuk memudahkan pengguna memasukkan data baru tanpa harus menghapusnya secara manual.

```
 private void bersih() {
        tfKodeMK.setText("");
        tfSKS.setText("");
        tfNamaMK.setText("");
        tfSemesterAjar.setText("");
        tampil();
    }
```

19.	Hasil eksekusi insert data

    ![image](https://github.com/user-attachments/assets/66534c4b-e338-466f-9956-7e31b350839f)

20.	Hasil eksekusi update data

    ![image](https://github.com/user-attachments/assets/622c504d-e1a6-4339-b1d9-1832859b1b21)

21.	Hasil eksekusi delete data

    ![image](https://github.com/user-attachments/assets/790b15df-ebef-4564-bc12-72ecb805009d)

    ![image](https://github.com/user-attachments/assets/7b364a04-060f-492e-b00b-d57055ab2df9)

22.	Hasil eksekusi cetak data

    ![image](https://github.com/user-attachments/assets/6765e299-18f1-427b-9de5-31bff6aff8f6)

23.	Hasil eksekusi upload data
    
a.	Pilih file yang akan diupload 

  ![image](https://github.com/user-attachments/assets/82b00695-785a-4468-8d9b-3746b6e7c3db)

b.	Jika berhasil akan muncul pesan seperti ini 

![image](https://github.com/user-attachments/assets/fca1cc08-bcb7-42f0-a13c-188c9111b27c)

c.	Data berhasil dimasukkan 

![image](https://github.com/user-attachments/assets/d2555911-113b-4043-9044-b39156713414)



    
























    








    







   
