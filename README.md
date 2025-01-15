# Teysar
-- phpMyAdmin SQL Dump
-- version 5.2.1
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Waktu pembuatan: 03 Jan 2025 pada 08.33
-- Versi server: 10.4.32-MariaDB
-- Versi PHP: 8.2.12

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `wm_aryani`
--

-- --------------------------------------------------------

--
-- Struktur dari tabel `ads`
--

CREATE TABLE `ads` (
  `id` int(11) NOT NULL,
  `title` varchar(255) NOT NULL,
  `content` text NOT NULL,
  `image_url` varchar(255) DEFAULT NULL,
  `is_active` tinyint(1) DEFAULT 1,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  `end_date` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data untuk tabel `ads`
--

INSERT INTO `ads` (`id`, `title`, `content`, `image_url`, `is_active`, `created_at`, `end_date`) VALUES
(44, 'PROMO! Special Hari Raya Natal dan Tahun Baru', 'Dapatkan dan nikmati beberapa menu dengan harga Rp. 7.000', '6741a7e84ecc5.jpg', 1, '2024-11-23 09:21:15', '2025-01-04 00:00:00');

-- --------------------------------------------------------

--
-- Struktur dari tabel `menu`
--

CREATE TABLE `menu` (
  `id` int(11) NOT NULL,
  `nama` varchar(255) NOT NULL,
  `harga` int(11) NOT NULL,
  `gambar` varchar(255) DEFAULT NULL,
  `kategori` enum('Makanan','Minuman','Camilan') DEFAULT NULL,
  `stok` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data untuk tabel `menu`
--

INSERT INTO `menu` (`id`, `nama`, `harga`, `gambar`, `kategori`, `stok`) VALUES
(18, 'Orak-Arik Telur', 10000, '673d8bfcbaf1b.jpg', 'Makanan', 0),
(19, 'Orak-Arik Ayam', 13000, '673d8c6fb5d44.jpg', 'Makanan', 8),
(20, 'Es Teh Manis', 3000, '673d8cdabb21e.jpg', 'Minuman', 5),
(21, 'Kopi Hitam Panas', 4000, '673d8d51cda7c.jpg', 'Minuman', 2),
(22, 'Es Jeruk', 3000, '673d8daa5e541.jpg', 'Minuman', 0),
(23, 'Air Es', 1000, '673d8e0f3b918.jpg', 'Minuman', 6),
(24, 'Mie Goreng Instan', 7000, '673d8e4f8b712.jpg', 'Makanan', 10),
(25, 'Nasi Telur', 10000, '673d8e852d69c.jpg', 'Makanan', 4),
(26, 'Ayam Bakar', 12000, '673e148ba10ec.jpg', 'Makanan', 5),
(31, 'Nasi Goreng Special', 15000, '67400c1ea12f2.jpg', 'Makanan', 0),
(32, 'Soto Ayam', 12000, '67400c6279e81.jpg', 'Makanan', 0),
(33, 'Ayam Penyet', 11000, '67400c9a37794.jpg', 'Makanan', 0),
(34, 'Tempe Mendoan', 1000, '67400cd112595.jpg', 'Camilan', 0),
(35, 'Tahu Crispy', 1000, '67400d086214d.jpg', 'Camilan', 0),
(36, 'Pisang Goreng Keju', 5000, '67400d51afb6a.jpg', 'Camilan', 0);

-- --------------------------------------------------------

--
-- Struktur dari tabel `notifications`
--

CREATE TABLE `notifications` (
  `id` int(11) NOT NULL,
  `message` text NOT NULL,
  `status` enum('unread','read') DEFAULT 'unread',
  `created_at` timestamp NOT NULL DEFAULT current_timestamp()
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data untuk tabel `notifications`
--

INSERT INTO `notifications` (`id`, `message`, `status`, `created_at`) VALUES
(184, 'Pesanan baru diterima dari Iza, Alamat: UDINUS. Produk yang dipesan: Ayam Bakar (x1). No Telepon: 081236262924. Metode Pembayaran: COD. Total harga: Rp 19.000', 'read', '2025-01-01 17:45:57'),
(185, 'Pesanan baru diterima dari Abe Kolin, Alamat: UDINUS. Produk yang dipesan: Nasi Telur (x1). No Telepon: 081236262924. Metode Pembayaran: COD. Total harga: Rp 17.000', 'read', '2025-01-01 17:52:03'),
(186, 'Pesanan baru diterima dari Nandar, Alamat: UDINUS. Produk yang dipesan: Air Es (x1). No Telepon: 081236262924. Metode Pembayaran: COD. Total harga: Rp 8.000', 'read', '2025-01-01 17:54:28'),
(187, 'Pesanan baru diterima dari Nandar, Alamat: UDINUS. Produk yang dipesan: Es Jeruk (x4). No Telepon: 081236262924. Metode Pembayaran: COD. Total harga: Rp 19.000', 'read', '2025-01-01 17:59:00'),
(188, 'Pesanan baru diterima dari testing, Alamat: UDINUS. Produk yang dipesan: Ayam Bakar (x1), Es Teh Manis (x1). No Telepon: 081236262924. Metode Pembayaran: COD. Total harga: Rp 22.000', 'read', '2025-01-03 07:06:09');

-- --------------------------------------------------------

--
-- Struktur dari tabel `sales_report`
--

CREATE TABLE `sales_report` (
  `id` int(11) NOT NULL,
  `nama_produk` varchar(255) DEFAULT NULL,
  `kuantitas` int(11) DEFAULT NULL,
  `total_harga` int(11) DEFAULT NULL,
  `tanggal_transaksi` timestamp NOT NULL DEFAULT current_timestamp(),
  `nama_penerima` varchar(255) DEFAULT NULL,
  `alamat` varchar(255) DEFAULT NULL,
  `telepon` varchar(15) NOT NULL,
  `metode_pembayaran` varchar(50) NOT NULL,
  `stat` enum('Sedang Diproses','Sedang Diantar','Selesai','Dibatalkan') DEFAULT 'Sedang Diproses',
  `user_id` int(11) DEFAULT NULL,
  `delete_at` datetime DEFAULT NULL,
  `status_pembayaran` enum('Belum bayar','Sudah bayar','Kedaluwarsa') NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data untuk tabel `sales_report`
--

INSERT INTO `sales_report` (`id`, `nama_produk`, `kuantitas`, `total_harga`, `tanggal_transaksi`, `nama_penerima`, `alamat`, `telepon`, `metode_pembayaran`, `stat`, `user_id`, `delete_at`, `status_pembayaran`) VALUES
(295, 'Ayam Bakar', 1, 12000, '2025-01-01 17:45:57', 'Iza', 'UDINUS', '081236262924', 'COD', 'Selesai', 79, NULL, 'Sudah bayar'),
(296, 'Nasi Telur', 1, 10000, '2025-01-01 17:52:03', 'Abe Kolin', 'UDINUS', '081236262924', 'COD', 'Selesai', 56, NULL, 'Sudah bayar'),
(297, 'Air Es', 1, 1000, '2025-01-01 17:54:28', 'Nandar', 'UDINUS', '081236262924', 'COD', 'Selesai', 77, NULL, 'Sudah bayar'),
(298, 'Es Jeruk', 4, 12000, '2025-01-01 17:59:00', 'Nandar', 'UDINUS', '081236262924', 'COD', 'Selesai', 77, NULL, 'Sudah bayar'),
(299, 'Ayam Bakar', 1, 12000, '2025-01-03 07:06:09', 'testing', 'UDINUS', '081236262924', 'COD', 'Selesai', 81, NULL, 'Sudah bayar'),
(300, 'Es Teh Manis', 1, 3000, '2025-01-03 07:06:09', 'testing', 'UDINUS', '081236262924', 'COD', 'Selesai', 81, NULL, 'Sudah bayar');

-- --------------------------------------------------------

--
-- Struktur dari tabel `users`
--

CREATE TABLE `users` (
  `id` int(11) NOT NULL,
  `username` varchar(50) NOT NULL,
  `email` varchar(100) DEFAULT NULL,
  `password` varchar(255) NOT NULL,
  `role` enum('user','admin') DEFAULT 'user'
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

--
-- Dumping data untuk tabel `users`
--

INSERT INTO `users` (`id`, `username`, `email`, `password`, `role`) VALUES
(49, 'Admin', 'albertog4taz28@gmail.com', '$2y$10$/b05WKA.ep/rjjGPDc1bZ.SACaXRPZLrDE75Iykqq2CLuqpvQevVy', 'admin'),
(56, 'Alberto', 'abekolin@outlook.com', '$2y$10$bIRH0bEunANUwYrkURs0xeuUHny9Hd1vzpnrM/mk4s4ow5Cuts7r.', 'user'),
(59, 'Alfario', 'alfariokolin@gmail.com', '$2y$10$BwkhQ1zEpo36ZduPdCL4UeYn2OY.R4aT5DVupT3/1ayCJcFk.ENQy', 'user'),
(68, 'Clementino', 'clementinokolin@gmail.com', '$2y$10$GUiy3e09u/MOWufENwyg4OJ1tXfMUAf2N5PjHgc/QKcsRHORi42U6', 'user'),
(72, 'rpl', 'rpl@gmail.com', '$2y$10$rePwVqIhO1R4ojHzysax3e70TmmzcMDCDxmLrSZ7ebvQFaAzHn9yK', 'admin'),
(76, 'kel5', 'kel5@gmail.com', '$2y$10$3s91R3K1WWBRKYy3U6mLKuKvlfix6MJQGYuMTQ2rAXYY3VbSSEj12', 'user'),
(77, 'Nandar', 'nandar@gmail.com', '$2y$10$BwarDVFGDcNhfm.6oyRG8Oix11u4JgvYVdz5XNdTxM/DJScrb8Hku', 'user'),
(78, 'Teysar', 'teysar@gmail.com', '$2y$10$gexm7sAJxStioN0bvaGULeVWerfHEzvEC9ATVQpKcpJvzbnLrtIgG', 'user'),
(79, 'Iza', 'iza@gmail.com', '$2y$10$see9NhVzuG8dTfnQqePPzOXb8hl2Np8YMpQYDMBvO7WwXXCIXAuI.', 'user'),
(80, 'test', 'test@gmail.com', '$2y$10$v/ngX7BCLVTAUsGv9w0uX.QXBWrOEaDJqEtbuUi/gV0c6WwCjHdpm', 'user'),
(81, 'testing', 'testing@gmail.com', '$2y$10$YQA4NnQj4up6Qr18eAVoDu.fYc5bgTqrIxlciLcGbUj9IOF5xlBOy', 'user'),
(82, 'teysarr', 'teysarr@gmail.com', '$2y$10$Hd32HD614GcmT.atKZ7hOe0uqcnoNTDy431alBlfWUixnwbpRwJ0e', 'user');

--
-- Indexes for dumped tables
--

--
-- Indeks untuk tabel `ads`
--
ALTER TABLE `ads`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `menu`
--
ALTER TABLE `menu`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `notifications`
--
ALTER TABLE `notifications`
  ADD PRIMARY KEY (`id`);

--
-- Indeks untuk tabel `sales_report`
--
ALTER TABLE `sales_report`
  ADD PRIMARY KEY (`id`),
  ADD KEY `fk_user_id` (`user_id`);

--
-- Indeks untuk tabel `users`
--
ALTER TABLE `users`
  ADD PRIMARY KEY (`id`);

--
-- AUTO_INCREMENT untuk tabel yang dibuang
--

--
-- AUTO_INCREMENT untuk tabel `ads`
--
ALTER TABLE `ads`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=46;

--
-- AUTO_INCREMENT untuk tabel `menu`
--
ALTER TABLE `menu`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=41;

--
-- AUTO_INCREMENT untuk tabel `notifications`
--
ALTER TABLE `notifications`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=189;

--
-- AUTO_INCREMENT untuk tabel `sales_report`
--
ALTER TABLE `sales_report`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=301;

--
-- AUTO_INCREMENT untuk tabel `users`
--
ALTER TABLE `users`
  MODIFY `id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=83;

--
-- Ketidakleluasaan untuk tabel pelimpahan (Dumped Tables)
--

--
-- Ketidakleluasaan untuk tabel `sales_report`
--
ALTER TABLE `sales_report`
  ADD CONSTRAINT `fk_user_id` FOREIGN KEY (`user_id`) REFERENCES `users` (`id`);
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
