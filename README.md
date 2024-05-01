# Tutorial 9
## Reflection
1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?
    - Unary merupakan metode paling sederhana di mana klien mengirim satu permintaan ke server dan menerima satu respons. Metode ini biasanya digunakan untuk operasi seperti mengambil data atau mengirimkan perintah tunggal.
    - Server Streaming digunakan ketika server perlu mengirimkan sejumlah respons secara berurutan kembali ke klien, setelah menerima satu permintaan. Metode ini biasanya digunakan untuk operasi seperti  pengiriman data yang terus-menerus seperti log atau feed data langsung.
    - Bi-directional Streaming memungkinkan klien dan server untuk saling mengirim stream data secara bebas dan independen. Metode ini biasanya digunakan untuk aplikasi yang membutuhkan komunikasi dua arah yang dinamis dan real-time, seperti chat, monitoring real-time, atau permainan interaktif di mana klien dan server sering bertukar data.


2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?  
   Dalam mengimplementasikan layanan gRPC di Rust, penting untuk memastikan autentikasi dan otorisasi yang aman untuk setiap request guna mengontrol akses berdasarkan peran pengguna. Keamanan transport juga penting dan dapat dilakukan enskripsi data yang ditransmisikan antara klien dan server, sehingga melindungi integritas dan kerahasiaan data. Selain itu, mempertimbangkan implementasi token seperti JWT untuk autentikasi dan otorisasi dapat membantu dalam validasi dan verifikasi identitas pengguna secara efisien dan aman.


3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?  
   Dalam implementasi bidirectional streaming dengan Rust gRPC untuk aplikasi chat, tantangan utama meliputi manajemen state yang kompleks akibat interaksi yang terus menerus antara klien dan server, serta kebutuhan untuk operasi asyncrhonus untuk mengirim dan menerima pesan secara bersamaan tanpa blokir.


4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services?  
   Dalam penggunaan `tokio_stream::wrappers::ReceiverStream` untuk layanan gRPC di Rust, keuntungan utamanya adalah kemampuan untuk mengelola data asynchronus secara efisien. Namun, pendekatan ini juga memiliki beberapa kekurangan, antara lain peningkatan kompleksitas dari error handling yang muncul dari operasi asynchronus hingga kesulitan dalam memastikan bahwa setiap data terautentikasi dan terotorisasi dengan benar.


5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?  
   Untuk meningkatkan code reuse and modularity dalam kode gRPC Rust, mendesain arsitektur dengan membuat interfaces yang diimplementasikan dalam proto sangat efektif dalam menjaga maintainability dan extensibility. Memecah kode menjadi berbagai modul yang terpisah berdasarkan fungsinya  juga sangat membantu dalam meningkatkan  code reuse and modularity


6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic?  
   Penanganan error yang untuk mengatasi masalah yang muncul selama transaksi, Validasi data pembayaran untuk memastikan semua informasi masuk adalah valid dan lengkap. Integrasi dengan sistem eksternal, seperti gateway pembayaran.


7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?  
   Penggunaan gRPC dapat meningkatkan modularitas dan efisiensi, memudahkan komunikasi antar layanan yang mungkin dibangun dengan bahasa pemrograman atau beroperasi di platform yang berbeda. gRPC juga memperkecil masalah interoperabilitas antar komponen yang berbeda, memperkuat integrasi lintas tech atau platform dengan lebih lancar dan efektif.


8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?  
   Dibandingkan dengan HTTP/1.1 atau HTTP/1.1 dengan WebSocket untuk REST APIs, HTTP/2, mempunyai kelebihan seperti multiplexing yang memungkinkan banyak permintaan dan respons melalui satu koneksi TCP, mengurangi latensi dan meningkatkan kecepatan muat halaman, kompresi header yang meningkatkan efisiensi bandwidth dan memungkinkan server push, di mana server dapat mengirim sumber daya tambahan tanpa permintaan dari klien. Namun, HTTP/2 juga memiliki kelemahan seperti overhead yang lebih tinggi dalam hal kinerja dan memori, serta kompleksitas implementasi yang lebih besar.


9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?  
   REST API kurang cocok untuk komunikasi real-time karena setiap interaksi membutuhkan permintaan yang terpisah, yang dapat menyebabkan latensi jika banyak permintaan yang dilakukan secara berurutan. Sebaliknya, gRPC dengan kemampuan streaming dua arah, memungkinkan server dan klien untuk saling mengirim dan menerima data secara real-time tanpa menunggu permintaan atau respons sebelumnya selesai. Ini meningkatkan responsivitas dan efektivitas dalam skenario komunikasi yang dinamis dan interaktif, seperti chat.


10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?  
    Protocol Buffers menyediakan struktur data yang menghasilkan struktur data yang terstruktur dan konsisten di seluruh sistem, komunikasi yang lebih efisien dan kinerja yang lebih baik. Namun, ini juga mengurangi fleksibilitas karena setiap perubahan pada skema memerlukan update dan recompile di kedua sisi klien dan server. Sedangkan, pendekatan schema-less dari JSON dalam REST API memberikan fleksibilitas lebih dalam manipulasi dan penggunaan data, memudahkan integrasi dan iterasi, tetapi dapat meningkatkan kompleksitas dan risiko kesalahan dalam pengelolaan data.


