import random

def jalankan_game():
    skor = 0
    nyawa = 3
    total_soal = 30
    
    print("=" * 45)
    print("      SELAMAT DATANG DI GAME HITUNG CEPAT     ")
    print("=" * 45)
    print("Rules:")
    print("1. Soal 1-10  : Maksimal angka 10 (+5 poin)")
    print("2. Soal 11-20 : Maksimal angka 30 (+10 poin)")
    print("3. Soal 21-30 : Maksimal angka 60 (+15 poin)")
    print("4. Kesempatan salah: Maksimal 3 kali")
    print("=" * 45)
    input("Tekan Enter untuk memulai game...")
    print("\n")

    for no_soal in range(1, total_soal + 1):
        if nyawa <= 0:
            print(" Game Over! Kamu sudah salah 3 kali.")
            break

        # Pengaturan tingkat kesulitan & skor berdasarkan nomor soal
        if no_soal <= 10:
            max_val = 10
            poin = 5
        elif no_soal <= 20:
            max_val = 30
            poin = 10
        else:
            max_val = 60
            poin = 15

        operator = random.choice(['+', '-', '*', '/'])
        
        # Logika pembentukan operand agar hasil/pembagian tetap bulat & simpel
        if operator == '/':
            b = random.randint(1, max_val)
            hasil_benar = random.randint(1, max_val)
            a = b * hasil_benar
        elif operator == '-':
            a = random.randint(1, max_val)
            b = random.randint(1, a)  # Supaya hasil tidak negatif
            hasil_benar = a - b
        else:
            a = random.randint(1, max_val)
            b = random.randint(1, max_val)
            if operator == '+':
                hasil_benar = a + b
            elif operator == '*':
                hasil_benar = a * b

        simbol_operator = 'x' if operator == '*' else (':' if operator == '/' else operator)

        # Loop sampai user memasukkan input angka yang valid
        while True:
            try:
                jawaban_user = int(input(f"Soal {no_soal}/{total_soal}: {a} {simbol_operator} {b} = "))
                break
            except ValueError:
                print(" Masukkan jawaban dalam bentuk angka bulat!")

        # Evaluasi Jawaban
        if jawaban_user == hasil_benar:
            skor += poin
            print(f" Benar! (+{poin} poin) | Skor saat ini: {skor}\n")
        else:
            nyawa -= 1
            print(f" Salah! Jawaban benar: {hasil_benar} | Sisa nyawa: {nyawa}\n")

    # Ringkasan Akhir
    print("=" * 45)
    print("                GAME SELESAI                  ")
    print("=" * 45)
    print(f" Total Skor Akhir Anda: {skor}")
    print("=" * 45)

if __name__ == "__main__":
    jalankan_game()# tugas_algopertemuan4
