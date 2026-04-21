# Modul-6-Concurrency

## Commit 1 Reflection notes

Pada milestone ini, saya mempelajari bagaimana membuat web server sederhana menggunakan Rust dengan memanfaatkan `TcpListener` untuk menerima koneksi dari client (browser). Program awal hanya menerima koneksi dan mencetak pesan “Connection established!”, yang menunjukkan bahwa server berhasil mendengarkan request dari browser pada alamat `127.0.0.1:7878`.

Selanjutnya, program dikembangkan dengan menambahkan fungsi `handle_connection` yang bertugas menangani setiap koneksi yang masuk. Pada fungsi ini digunakan `BufReader` untuk membaca data dari `TcpStream`, kemudian method `.lines()` digunakan untuk membaca request HTTP baris per baris. Data tersebut dikumpulkan ke dalam sebuah `Vec<String>` hingga menemukan baris kosong yang menandakan akhir dari header HTTP.

Dari hasil output, terlihat bahwa browser mengirimkan request dalam format HTTP, seperti:

- `GET / HTTP/1.1`
- `Host`, `User-Agent`, dan header lainnya

Hal ini memberikan pemahaman bahwa komunikasi antara browser dan server menggunakan protokol HTTP berbasis teks, dan server perlu memproses request tersebut untuk memberikan response yang sesuai.

Selain itu, saya juga memahami bahwa browser dapat mengirim beberapa request sekaligus (retry), sehingga pesan “Connection established!” bisa muncul lebih dari satu kali. Ini merupakan perilaku normal dari browser.