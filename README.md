# SkandaProject
FESTIKA JAWA TIMUR 2025-Bidang Lomba AREK AI-SMART ABSENSI KELAS SKANDA DENGAN PEMROGRAMAN PYTHON

#Full Code Program
import datetime

def menu():
    print("\n=== SMART ABSENSI KELAS SKANDA ===")
    print("1. Tambah Absensi")
    print("2. Lihat Rekap Absensi")
    print("3. Keluar")

def tambah_absensi():
    nama = input("Masukkan nama siswa: ")
    print("Pilih status kehadiran:")
    print("1. Hadir\n2. Izin\n3. Sakit\n4. Alpa")
    pilihan = input("Masukkan pilihan (1-4): ")

    status = {"1":"Hadir","2":"Izin","3":"Sakit","4":"Alpa"}.get(pilihan,"Tidak Valid")
    tanggal = datetime.date.today()

    if status != "Tidak Valid":
        with open("absensi.txt","a") as f:
            f.write(f"{tanggal} | {nama} | {status}\n")
        print(" Absensi berhasil dicatat!")
    else:
        print(" Pilihan tidak valid.")

def lihat_rekap():
    try:
        with open("absensi.txt","r") as f:
            print("\n=== REKAP ABSENSI ===")
            print(f.read())
    except FileNotFoundError:
        print("Belum ada data absensi.")

while True:
    menu()
    pilihan = input("Pilih menu (1-3): ")
    if pilihan == "1":
        tambah_absensi()
    elif pilihan == "2":
        lihat_rekap()
    elif pilihan == "3":
        print("Terima kasih telah menggunakan SMART ABSENSI SKANDA!")
        break
    else:
        print("Pilihan tidak valid, coba lagi.")
