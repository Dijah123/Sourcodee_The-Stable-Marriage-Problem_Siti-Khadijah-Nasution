def stable_marriage(men_prefs, women_prefs):
    n = len(men_prefs)  # Jumlah pria dan wanita
    free_men = list(men_prefs.keys())  # Daftar pria yang belum bertunangan
    engaged = {}  # Pasangan pertunangan {wanita: pria}
    men_next_proposal = {man: 0 for man in men_prefs}  # Indeks proposal berikutnya untuk setiap pria

    # Balik preferensi wanita agar mudah menentukan pilihan
    women_ranking = {w: {m: i for i, m in enumerate(women_prefs[w])} for w in women_prefs}

    while free_men:
        man = free_men[0]  # Ambil pria pertama yang masih bebas
        woman = men_prefs[man][men_next_proposal[man]]  # Wanita yang dilamar
        men_next_proposal[man] += 1  # Naikkan indeks proposal pria

        if woman not in engaged:
            # Jika wanita belum bertunangan, langsung terima lamaran
            engaged[woman] = man
            free_men.pop(0)
        else:
            current_partner = engaged[woman]
            # Tentukan apakah wanita lebih suka pria baru daripada pasangannya saat ini
            if women_ranking[woman][man] < women_ranking[woman][current_partner]:
                engaged[woman] = man
                free_men.pop(0)
                free_men.append(current_partner)  # Pasangan lama jadi lajang lagi

    # Balik pasangan agar format output sesuai
    return {man: woman for woman, man in engaged.items()}

# Contoh preferensi pria dan wanita
men_prefs = {
    "A": ["X", "Y", "Z"],
    "B": ["Y", "X", "Z"],
    "C": ["X", "Y", "Z"]
}

women_prefs = {
    "X": ["B", "A", "C"],
    "Y": ["A", "B", "C"],
    "Z": ["A", "B", "C"]
}

# Jalankan algoritma
matches = stable_marriage(men_prefs, women_prefs)

# Cetak hasil pencocokan
print("Hasil Pencocokan Stabil:")
for man, woman in matches.items():
    print(f"{man} - {woman}")
