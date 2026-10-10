<div align="center">

<img src="rasmlar/banner.svg" alt="BOZOR KUZATUV" width="100%"/>

**Viloyatdagi bozorlar, turargohlar, to'yxonalar, karyerlar va hosil qabul punktlarini bitta markazdan real vaqtda kuzatish tizimi:** tushum, oqim, kamera holati va aloqa uzilishi bir ekranda ko'rinadi, muammo bo'lsa Telegram orqali xabar keladi.

![Python](https://img.shields.io/badge/Python-3.12%20stdlib-3776AB?logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-WAL-003B57?logo=sqlite&logoColor=white)
![SSE](https://img.shields.io/badge/jonli%20oqim-SSE-0ea5e9)
![Docker](https://img.shields.io/badge/Docker-Caddy-2496ED?logo=docker&logoColor=white)
![Telegram](https://img.shields.io/badge/Telegram-bot%20%C2%B7%202FA-26A5E4?logo=telegram&logoColor=white)
![Sinovlar](https://img.shields.io/badge/sinovlar-964%20ta%20o'tadi-2ea44f)

</div>

---

## Bir qarashda

<div align="center">
<img src="rasmlar/intro.gif" alt="Kirish animatsiyasi: tuman chegaralari chiziladi, obyektlar ulanadi, keyin bozorlar paneli ochiladi" width="85%"/>
</div>

Har bir obyekt (bozor kassasi, turargoh shlagbaumi, karyer tarozisi) markazga o'z ma'lumotini yuboradi. Markaz obyektni to'rt holatdan birida ko'rsatadi:

| Holat | Ma'nosi |
|---|---|
| 🟢 **Onlayn** | Ma'lumot kelyapti, kameralar javob beryapti |
| 🟡 **Nosozlik** | Obyekt ishlayapti, lekin kameralarning bir qismi jim |
| 🔴 **Oflayn** | 180 soniyadan beri aloqa yo'q. Raqamlar uzilish paytida «muzlaydi», Telegram'ga xabar ketadi |
| ⚪ **Ulanmagan** | Obyekt reyestrda bor, hali ulanmagan. Uning raqami **ko'rsatilmaydi** (0 emas) |

**Halollik qoidasi:** manbasi yo'q ko'rsatkich hech qachon «0» bo'lib chiqmaydi, uning o'rnida «—» va «manba yo'q» yoziladi. Aks holda nol «hammasi naqd» yoki «hech kim kelmadi» deb o'qilishi mumkin edi.

## Asosiy imkoniyatlar

| | |
|---|---|
| 🏪 **7 xil obyekt** | Oziq-ovqat bozori, avtoturargoh, to'yxona, chorva bozori, karyer, mashina bozori, jarima maydonchasi. Yangi bo'lim panelning o'zidan qo'shiladi (nom, prefiks, xulq-shablon, shakl, rang), dasturchi kerak emas |
| 🔌 **Vendor API** | Kassa, ANPR yoki CRM dasturi har hodisada bitta so'rov yuboradi: `POST /api/v1/hodisa`. Bearer token, ixtiyoriy HMAC imzo, takroriy chek ikki marta sanalmaydi (409). Eski kassalar uchun oddiy GET-havola ham bor |
| 📷 **Kamera nazorati** | Obyekt kompyuteridagi agent 12 belgili faollashtirish kaliti bilan ulanadi. Har kameradan 45 soniyada bitta kadr keladi, kamera ochilganda jonli rejimga o'tadi. Video markazda saqlanmaydi |
| ⛰️ **Karyer: pulsiz nazorat** | Karyerda pul ko'rsatilmaydi, chunki uning ishonchli manbasi yo'q. Buning o'rniga yuk (tonna), reyslar va **hujjatsiz chiqishlar** kuzatiladi. Hujjatsiz chiqqan mashina qizil rangda turadi |
| 🚗 **Avtoturargoh** | Kirdi, chiqdi, ichkarida turgan mashinalar, tushum va to'lov usuli. Sig'imi to'ldirilmagan obyektda bandlik foizi chiqmaydi |
| 🌾 **Hosil qabuli** | Paxta va g'alla qabul punktlari: tarozi (COM port), 4 kamera, har tortishning brutto, tara va netto chizig'i, 14 ta avtomatik tekshiruv. Punkt agenti internet uzilganda navbatda saqlaydi |
| 🏛️ **Situatsion markaz** | Elektr, gaz, suv, ijtimoiy himoya, bandlik va murojaatlar tuman kesimida. Uzilishlar reyestri va xaritasi, topshiriqlar va ularning muddati |
| 👥 **6 rol** | Super admin, admin, tuman hisobi, soha tashkiloti, kuzatuvchi, murojaat operatori. Tuman hisobi faqat o'z tumanini ko'radi, filtr **serverda** ishlaydi (jonli oqim ham) |
| 🔐 **Xavfsizlik** | Telegram orqali ikki bosqichli kirish, sessiyani masofadan uzish, urinishlar cheklovi, CSV ga chiqariladigan audit jurnali |
| 📈 **Bozor lentasi** | Markaziy bank kurslari va tovar-xomashyo birjasi narxlari panel tepasida yuguradi |

## Ekranlar

<table>
<tr>
<td width="50%"><img src="rasmlar/02_bozorlar.png" alt="Bozorlar: umumiy ko'rinish"/><br/><sub><b>Ichki bozorlar</b> — bo'limlar bo'yicha holat, bugungi tushum, jonli hodisalar</sub></td>
<td width="50%"><img src="rasmlar/01_situatsion_markaz.png" alt="Situatsion markaz"/><br/><sub><b>Situatsion markaz</b> — kommunal va ijtimoiy sohalar tuman kesimida</sub></td>
</tr>
<tr>
<td><img src="rasmlar/03_xarita.png" alt="Viloyat xaritasi"/><br/><sub><b>Viloyat xaritasi</b> — sputnik qatlami, obyektlar holat va tur bo'yicha</sub></td>
<td><img src="rasmlar/04_bozor_sahifasi.png" alt="Bozor sahifasi"/><br/><sub><b>Bozor sahifasi</b> — tushum, to'lov usullari, 7/30/90 kunlik taqqoslash</sub></td>
</tr>
<tr>
<td><img src="rasmlar/05_kameralar.png" alt="Kameralar"/><br/><sub><b>Kameralar</b> — oxirgi kadr va kamera holati (suratlar sxematik namuna)</sub></td>
<td><img src="rasmlar/06_avtoturargoh.png" alt="Avtoturargoh"/><br/><sub><b>Avtoturargoh</b> — kirdi, chiqdi, ichkarida, tushum</sub></td>
</tr>
<tr>
<td><img src="rasmlar/07_chorva_bozori.png" alt="Chorva bozori"/><br/><sub><b>Chorva bozori</b> — kirgan mollar, kirish yig'imi</sub></td>
<td><img src="rasmlar/08_karyer.png" alt="Karyerlar"/><br/><sub><b>Karyerlar</b> — tonna, reys, hujjatsiz chiqish (pul ko'rsatilmaydi)</sub></td>
</tr>
<tr>
<td><img src="rasmlar/09_topshiriqlar.png" alt="Topshiriqlar"/><br/><sub><b>Topshiriqlar</b> — mas'ul, muddat, ijro holati</sub></td>
<td><img src="rasmlar/10_integratsiya.png" alt="Integratsiya API"/><br/><sub><b>Integratsiya · API</b> — har bo'lim uchun tayyor so'rov namunasi</sub></td>
</tr>
<tr>
<td><img src="rasmlar/11_hosil_umumiy.png" alt="Hosil qabuli"/><br/><sub><b>Hosil qabuli</b> — punktlar, bugungi qabul, ochiq holatlar</sub></td>
<td><img src="rasmlar/12_hosil_tortish.png" alt="Tortish kartasi"/><br/><sub><b>Tortish kartasi</b> — 4 kamera dalili, brutto/tara, namlik va konditsion vazn</sub></td>
</tr>
<tr>
<td colspan="2"><img src="rasmlar/13_hosil_holatlar.png" alt="Avtomatik tekshiruvlar"/><br/><sub><b>14 avtomatik tekshiruv</b> — kamera o'chgan, internetsiz qabul, qiyoslash muddati o'tgan, raqam tanilmagan va boshqalar</sub></td>
</tr>
</table>

> Suratlardagi barcha obyektlar, raqamlar, davlat raqamlari va fermer nomlari **namuna ma'lumot**. Kamera kadrlari sxematik rasm.

## Arxitektura

```mermaid
flowchart LR
    K[Kassa / ANPR / CRM<br/>obyekt dasturi] -- "hodisa · puls<br/>Bearer token, ixtiyoriy HMAC" --> API
    A[Kamera agenti<br/>faollashtirish kaliti] -- "JPEG kadr, 45 s" --> API
    H[Hosil punkti agenti<br/>tarozi COM · 4 kamera] -- "tortish va dalil" --> API
    S[Soha tashkilotlari<br/>elektr · gaz · suv] -- "soha tokeni" --> API
    subgraph M[Markaz · Docker]
        API[Qabul API<br/>/api/v1] --> DB[(SQLite WAL)]
        DB --- W[Panel serveri<br/>Python stdlib]
        Q[Qorovul<br/>180 s → oflayn] --- DB
    end
    W -- "SSE jonli oqim" --> P[Nazorat paneli]
    Q -- "holat o'zgarsa" --> T[Telegram bot]
```

- **Tashqi kutubxonasiz server:** faqat Python standart kutubxonasi (`ThreadingHTTPServer`, `sqlite3`). Panel — bitta HTML fayl, freymvorksiz JavaScript.
- **Ikki domen, bitta jarayon:** panel va qabul API alohida domenda, Caddy orqasida bitta konteynerga boradi. Konteyner tashqariga port ochmaydi.
- **Yangi bo'lim — alohida fayl:** masalan, «Hosil qabuli» panel shabloniga tegmasdan alohida JS modul sifatida ulanadi.

## Sifat

**964 ta avtomatik sinov, 0 xato** (toza vaqtinchalik bazada ishga tushirib sanaldi):

| To'plam | Sinov |
|---|---:|
| Regressiya (butun zanjir) | 45 |
| Telegram ogohlantirishlari (soxta bot serveri bilan) | 28 |
| Qabul API | 151 |
| Baza | 125 |
| Rol, sessiya, token, audit | 150 |
| Fuqaro murojaatlari | 44 |
| Tashqi manbalar | 31 |
| Elektr tarmog'i | 48 |
| Statistika va tahlil | 36 |
| Bozor lentasi | 53 |
| Panel (headless Chrome) | 153 |
| Hosil qabuli API | 63 |
| Hosil punkti agenti (virtual COM port) | 37 |

- Baza auditi jamlanma raqamlarini **mustaqil SQL** bilan qayta hisoblab solishtiradi: kod o'zini o'zi tasdiqlamaydi.
- Panel auditi ekrandagi raqamlarni server javobi bilan solishtiradi va sessiya davomida JS xatosi yo'qligini tekshiradi.

## Texnologiyalar

Python 3.12 (stdlib) · SQLite (WAL) · Server-Sent Events · vanilla JavaScript + SVG · Esri sputnik qatlami · Docker + Caddy · Telegram Bot API · ffmpeg (punkt agenti) · Playwright (sinovlar)

## Jonli

🌐 [kuzatuv.geonazorat.uz](https://kuzatuv.geonazorat.uz) — xizmat kirishi (login talab qilinadi)

---

<div align="center">

**Manba kodi yopiq.** Namoyish yoki hamkorlik bo'yicha: Telegram [@Humoyun_Davronov](https://t.me/Humoyun_Davronov)

<sub>Muallif — Humoyun Davronov</sub>

</div>
