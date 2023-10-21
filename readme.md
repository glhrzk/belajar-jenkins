
![Logo](https://www.jenkins.io/images/logo-title-opengraph.png)
## Roadmap

- [Jenkins Dasar](https://linktodocumentation)

- [Jenkins Pipeline](https://linktodocumentation)

- [Jenkins Shared Library](https://linktodocumentation)


# Belajar Jenkins Dasar 

Catatan pribadi yang akan digunakan untuk kedepannya.

## Jenkins Dasar
 Jenkins adalah automation server yang opensource, yang dibuat dari bahasa JAVA.

- Jenkins Data

Jenkins tidak membutuhkan database untuk menyimpan seluruh konfigurasi dan datanya.
jenkins akan secara otomatis membuat folder .jenkins di ~/ (home) directory system operasi kita.

- Job

Job adalah panggilan untuk tugas automatin di Jenkins
saat pertama kali menginstall jenkis, tidak ada satupun job yang ada.


- Plugin

plugin Jenkins itu komponen yang bisa lu tambahin ke Jenkins buat ngebikin Jenkins lebih canggih.
Dengan pake plugin, lu bisa integrasikan Jenkins sama berbagai macam tools, teknologi, atau layanan lain.

- Build Step

menambahkan konfigurasi job untuk menambahkan step yang kita mau, bisa lebih dari satu.

- Post Build Action

fitur ini biasanya digunakan untuk memberitahu status sebuah job ketika proses build telah selesai, contoh mengirim notifikasi ke email, chat dan sejenisnya.

- Copy Job

adalah fitur yang bisa digunakan untuk membuat job baru dengan cara copy dari job yang sudah ada, terkadang banyak sekali konfigurasi yang sama antara job yang satu dengan job yang lainnya, contohnya build step atu post build action

- Schedule Job

pada defaultnya job tidak akan start/mulai tanpa di trigger, kita bisa membuat Schedule job agar bisa kita build di waktu waktu tertentu.
kita bisa menambahkan cronjob di Build Triggers -> Build periodically

- Poll SCM

mirip dengan Schedule job, tetapi hanya akan menjalankan jobnya, ketika terjadi perubahan (Changes) di source code, jika tidak ada perubahan maka job tidak akan dijalankan

- Disable JOB

jika ingin menghentikan Schedule / cron, lebih baik disable projek/jobnya, jika di disable tombol build now nya menghilang.

- Jenkins Environment Variable

 jenkins memiliki /env-vars.html yang bisa kita panggil dan digunakan di dalam buildstep/execute 

- Global Environment Variable

 kita juga bisa menambahkan env variable tambahakan ke Jenkins, env yang kita tambahakan otomatis akan terintegrasi secara global dan bisa digunakan di semua job.
 Manage Jenkins -> Configure System -> Global Properties -> Environment Variables
 
- Build Parameter (This project is parameterized?)

 adalah fitur dimana jenkins meminta input user sebelum menjalankan job, bisa diterapkan jika ingin menentukan job akan di deploy kemana (dev/prod).
jenis input data: boolean, string, choic, secret dll.
input data yang diberikan user, secara otomatis bisa kita ambil seperti env di build step.

- Discard Old Build (Discard old builds)

jenkins menyimpan semua history build di folder .jenkins HOME directory, secara default jenkins akan menyimpan semua history job selamannya, hal ini akan mengakibatkan kehabisan ruang penyimpanan.
jenkins memiliki fitur penghapusan riwayat yang lama secara otomatis baik itu menggunakan hari atau jumlah build.
jika kita mengaktifkan fitur ini jenkins secara otomatis akan melakukan pengecekan ketika job selesai dijalankan.

- Build Executor

Jenkins menjalankan semua job di dalam Executor, secara default jenkins menggunakan 2 executor untuk menjalankan job.
saat semua executor sedang sibuk maka job akan dijalankan harus menunggu terlebih dahulu sampai executor tersedia.
kita bisa mengubah executordari menu Manage Jenkins -> Configure Jenkins -> #of Executor

- Anonymous readonly

adalah fitur untuk mengaktifkan orang lain (tanpa login) bisa melihat job yang ada, berguna jika untuk project opensource

- User Management

pada defaultnya jenkins tidak memiliki kemampuan untuk mengatur roles antar user atau pun login dll, kita bisa memanfaatkan plugin yang ada.
contoh plugin: 1.role-base-authorization-strategy 2.saml 3.google-login 4.github-oauth 5.gitlab-oauth dll

- Trigger Build Remotely

ini adalah fitur untuk menjalankan build secara remote, remote dalam artian tanpa harus membuka/mengakses web jenkins.
fitur ini cocok ketika misal kita membuat bot, dan bot tersebut bisa memerintahkan jenkins untuk menjalankan job yang kita minta.
cara kerja fitur ini menggunakan HTTP POST dan mengirimkan Token tersebut.

- View

adalah grup yang berisi kumpulan job job tertentu.
case ini dipakai jika sudah terlalu banyak job yang ada.

- Node / Agent

sama seperti node di kubernetes/ocp atau bisa dibilang node worker. dengan menambahkan node jenkins, kita tidak perlu melakukan setup job secara manual, semuanya akan dikerjakan otomatis oleh jenkins ke semua node yang ada.
