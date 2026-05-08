Ro'yxatingizdagi 29 ta terminni birma-bir sanab oling. Hech qaysi biri tushib qolmaydi va ularning barchasi aynan "A birjadan arzonroq olib, B birjaga qimmatroq sotish" (Arbitraj) mantig'iga moslashtirilgan holda tushuntiriladi.
​Mana bizning to'liq jangovar arsenalimiz:
​1. Flashloan
​Nimaligi: Garovsiz, atigi bitta blok (soniya) ichida olinib qaytariladigan o'ta yirik miqdordagi kredit.
​Biz qanday ishlatamiz: A birjadan B birjaga arbitraj qilishda katta foyda olish uchun bizga katta pul kerak. Botimiz 100 000$ lik WBNB ni qarzga oladi, A da xarid qiladi, B da sotadi, foydani olib qarzni yopadi — bularning barchasi bitta tranzaksiya ichida yuz beradi.
​2. Smartkontrakt
​Nimaligi: Blokcheyn tarmog'ida yashovchi va pullarni boshqaruvchi kod.
​Biz qanday ishlatamiz: Bu bizning xavfsiz "qo'llarimiz". Go bot arbitrajni topsa, aynan shu kontraktga o'q uzishni buyuradi. Kontrakt Flashloan oladi, A va B birjalarda ayirboshlashni amalga oshiradi va agar foyda chiqmay qolsa, butun jarayonni revert (bekor) qilib kapitalni asrab qoladi.
​3. Private kanallar
​Nimaligi: Umumiy tranzaksiyalar hovuzini (Mempool'ni) aylanib o'tuvchi yopiq aloqa tarmoqlari (masalan, BloXroute).
​Biz qanday ishlatamiz: Arbitraj buyrug'imizni raqobatchi qaroqchilar ko'rib qolib, o'zlashtirib olmasligi uchun tranzaksiyani to'g'ridan-to'g'ri blok yasovchi validatorlarning stoli ustiga eltib berishda ishlatamiz.
​4. Go bot
​Nimaligi: Dasturning asosiy "miyasi", tashqi muhitni kuzatuvchi va buyruq beruvchi markaz.
​Biz qanday ishlatamiz: A va B birjalardagi narxlarni millisoniya tezligida uzluksiz tahlil qilib turuvchi, spred (foyda keltiruvchi narx farqi) paydo bo'lishi bilan simulyatsiya qilib, darhol arbitrajni boshlashga buyruq beruvchi backend.
​5. Noda
​Nimaligi: BSC tarmog'ining to'liq ma'lumotlar bazasini o'z ichiga olgan va yangilab turuvchi dastur (Geth).
​Biz qanday ishlatamiz: A va B birjalardagi eng so'nggi narx o'zgarishlarini hech kimdan (RPC provayderlardan) kutmasdan, 0 kechikish bilan to'g'ridan-to'g'ri o'z serverimizda qabul qilib olish uchun ishlatamiz.
​6. Qaroqchi botlar
​Nimaligi: Sizning tranzaksiyangizdan oldinroq o'z tranzaksiyasini tiqishga urinadigan yirtqich botlar.
​Biz qanday ishlatamiz (himoyalanamiz): Arbitraj imkoniyatimizni ular bizdan o'g'irlab olmasligi uchun "Private kanallar" orqali yashirinish va "Smartkontrakt" kodini tushunarsiz qilib yozish (obfuskatsiya) orqali ularni chalg'itamiz.
​7. Foydani hisoblash formulasi
​Nimaligi: Daromadni aniqlovchi qat'iy matematik formula.
​Biz qanday ishlatamiz: Go bot doimiy ravishda quyidagicha hisoblaydi: B_sotuv - A_xarid - Flashloan_foizi - Gaz_xarajati - Pora = Sof_foyda. Agar Sof foyda noldan katta bo'lsa, arbitraj ishga tushadi.
​8. Local simulyatsiya (real jarayon oldidan)
​Nimaligi: Tranzaksiyani haqiqiy tarmoqqa yuborishdan oldingi virtual "Test-drayv".
​Biz qanday ishlatamiz: Arbitrajimiz rostdan ham muvaffaqiyatli bo'ladimi yoki B birjadagi narx o'zgarib qoldimi? Pulni va gazni xavf ostiga qo'ymaslik uchun, uni 1 ms ichida botimiz xotirasida yurgizib, formula to'g'riligini tasdiqlaymiz.
​9. Yul
​Nimaligi: Smartkontrakt darajasida ishlatiladigan Assembly (quyi darajali) til.
​Biz qanday ishlatamiz: A va B birjalarning rasmiy "Router" lariga murojaat qilsak komissiya qimmatlashadi. Shu sababli arbitrajimiz o'ta arzon bo'lishi uchun Pair kontraktlarning xotira manzillariga to'g'ridan-to'g'ri Yul orqali yozamiz (gas-optimization).
​10. Hexadecimal kodlar
​Nimaligi: 16-lik sanoq tizimidagi tushunarsiz kompyuter kodlari (0x...).
​Biz qanday ishlatamiz: Mempool'dan kelayotgan raqobatchi yoki oddiy foydalanuvchilarning tranzaksiyalarini tutib, ular BSC tarmog'ida qaysi tokenni qayerga o'tkazayotganini tahlil qilish (narx qayerga yurishini oldindan bilish) uchun o'qiymiz.
​11. Whitelist (tokenlar uchun)
​Nimaligi: Qopqoni bo'lmagan, ishonchli va yirik pul aylanmasiga ega juftliklar ro'yxati.
​Biz qanday ishlatamiz: Go botimiz faqat shu ro'yxatga kiritilgan tokenlar o'rtasida (masalan, WBNB/USDT) arbitraj izlaydi. Boshqa axlat tokenlarni butunlay rad etib, vaqt va protsessor quvvatini tejaydi.
​12. Hujum strategiyasi (Siz bilgan maxfiy variant)
​Nimaligi: Arbitrajni amalga oshirishning betakror, algoritmik mantiqiy ketma-ketligi.
​Biz qanday ishlatamiz: Go botning asosiy qaror qabul qilish blokida bozordagi tayyor (sendvich/front-run) shablonlar o'rniga, shaxsan siz ishlab chiqqan maxfiy yo'nalish mantig'ini o'rnatamiz. Bu bizning asosiy ustunligimiz bo'ladi.
​13. ABI
​Nimaligi: Smartkontraktlar uchun tarjimon (Application Binary Interface).
​Biz qanday ishlatamiz: Hexadecimal kodlarni "A birjadan X miqdorda Y tokenni olyapti" degan tushunarli ma'lumotga o'girib, arbitraj imkoniyatini aniq hisob-kitob qilish uchun lug'at sifatida ishlatamiz.
​14. WBNB
​Nimaligi: BNB ning o'ta tez almashtirilishga moslangan o'ralgan (wrapped) talqini.
​Biz qanday ishlatamiz: Arbitraj dvigatelining asosiy "qoni". Barcha Flashloanlar va A dan B ga qiymat ko'chirishlar tez va arzon bo'lishi uchun faqat WBNB orqali bajariladi.
​15. Nonce menejmenti
​Nimaligi: Bitta manzildan chiquvchi tranzaksiyalarning majburiy tartib raqami.
​Biz qanday ishlatamiz: A-B va C-D birjalarda bir vaqtda 2 ta arbitraj chiqib qolsa, Go botimiz ikkita tranzaksiyani chalkashtirmasdan, tartib bilan (masalan, Nonce 101, Nonce 102) tarmoqqa to'g'ri uzatishini ta'minlaymiz.
​16. Slippage
​Nimaligi: Operatsiya bajarilayotganda narxning sirpanishi (o'zgarish foizi).
​Biz qanday ishlatamiz: Arbitrajda marja (foyda) juda kichik. Shuning uchun smartkontraktda slipajni qat'iy nolga (0%) yoki faqat bizga foyda qoldiradigan darajaga qulflaymiz. Salgina salbiy o'zgarishda darhol Revert qilinadi.
​17. block.coinbase.transfer
​Nimaligi: Blokni yopayotgan konchiga (validatorga) bevosita mablag' o'tkazish komandasi.
​Biz qanday ishlatamiz: Arbitrajdan tushgan katta foydaning bir qismini ushbu kod yordamida validatorga "pora" sifatida beramiz, shunda u qaroqchilarni surib qo'yib, bizning tranzaksiyani birinchi bo'lib qabul qiladi.
​18. Qopqonlardan himoya white list taminlaydi
​Nimaligi: Xavfsizlik dambasi. Honeypot (sotib bo'lmaydigan) va yuqori soliq qopqonlari bor tokenlarga qarshi himoya.
​Biz qanday ishlatamiz: Botimiz bu xavfli tokenlarni aniqlashga vaqt (simulyatsiya) sarflamasligi uchun, tranzaksiya oqimini faqat Whitelist filtridan o'tkazamiz, qolgan barchasi axlat qutisiga ketadi.
​19. IPC ulanishi
​Nimaligi: Server ichidagi dasturlar orasidagi to'g'ridan-to'g'ri operativ xotira aloqasi.
​Biz qanday ishlatamiz: Geth nodasi va Go botimiz websocket (ws://) yoki HTTP orqali gaplashib millisoniyalarni yo'qotmasligi uchun, ma'lumotni to'g'ridan-to'g'ri geth.ipc orqali 0 kechikish bilan o'qiymiz.
​20. Pair sync event
​Nimaligi: Birjalardagi (Pair) hovuzlarda qancha token qolganini o'zgarish soniyasida ma'lum qiluvchi signal.
​Biz qanday ishlatamiz: Go bot A va B birjaning zaxiralarini har safar so'rab bilmaydi. Bot Sync eventlarini eshitib, to'g'ridan-to'g'ri o'zining RAM xotirasidagi narxlar jadvalini doimiy avtomatik yangilab boradi.
​21. EIP-1559
​Nimaligi: Tarmog'ining yangi avlod komissiya mexanizmi (Base Fee va Priority Fee).
​Biz qanday ishlatamiz: Arbitraj tranzaksiyasi o'tishi uchun tarmoqqa qancha tayanch gaz va validatorga qancha ustama berishni eng optimal tarzda Go bot orqali hisoblashda ishlatamiz.
​22. RLP (Recursive Length Prefix)
​Nimaligi: Ma'lumotlarni tarmoq bo'ylab kompyuter tilida zich qadoqlash formati.
​Biz qanday ishlatamiz: Mempool'dan birinchi bo'lib oqib keladigan yopiq baytlar oqimini ochib (decode), keyinchalik ABI orqali o'qish mumkin bo'lgan holatga keltirish uchun ishlatamiz.
​23. Goroutines va Mutex (RWMutex)
​Nimaligi: Go tilidagi multithreading (ko'p yadroli parallel ishlash) texnologiyasi.
​Biz qanday ishlatamiz: Bot bir vaqtda ham A birjani eshitishi, ham B birjani tahlil qilishi va hujumga simulyatsiya qilishini ta'minlash uchun Goroutines ishlatamiz. O'qilayotgan xotira ma'lumotlari adashib ketmasligi (crash) ni RWMutex bilan qulflab-ochamiz.
​24. In-Memory StateDB
​Nimaligi: Noda dagi blokcheyn xotirasining uzib olinib Go botning o'ziga o'rnatilgan nusxasi.
​Biz qanday ishlatamiz: Arbitraj simulyatsiyasini o'tkazishda bot har safar nodaga yalinib IPC orqali eth_call qilmasligi uchun, tahlilni to'g'ridan-to'g'ri o'z ichidagi StateDB baza orqali mikrosiniyalarda tekshirib oladi.
​25. Custom EVM (REVM)
​Nimaligi: Ethereum Virtual Machinasining o'ta tez ishlaydigan va xavfsizlik cheklovlari olib tashlangan (Rust'da yozilgan) varianti.
​Biz qanday ishlatamiz: Botimiz In-Memory StateDB ustida arbitraj tranzaksiyamiz qanday yakunlanishini (foydani) standart EVM'dan ko'ra bir necha o'n marta tezroq simulyatsiya qilishi uchun Go kodga ulab ishlatamiz.
​26. Direct Peering / Sentry Nodes (To'g'ridan-to'g'ri ulanish)
​Nimaligi: Nodani geografik va tarmoq jihatdan bevosita "Validatorlar" (asosiy konchilar) bilan yuzma-yuz ulash.
​Biz qanday ishlatamiz: A yoki B birjada kimdir narxni o'zgartirganini oddiy foydalanuvchilardan oldinroq eshitish va tayyor arbitraj hujumimizni validatorga qisqa yo'ldan (birinchi bo'lib) yuborish uchun infratuzilmamizni shunga sozlaymiz.
​27. Bloom Filters (tezkor filtrlash)
​Nimaligi: Ma'lum bir manzil ro'yxatda bormi-yo'qligini protsessorni qiynamasdan aytib beruvchi matematik elak.
​Biz qanday ishlatamiz: Mempool'dan soniyaga kelayotgan minglab axlat tranzaksiyalar bizning "Whitelist"dagi juftliklarimizga taalluqlimi yoki yo'qligini, nol tsikl (O(1) tezlik) bilan filtrlash uchun Go botga o'rnatamiz.
​28. Access Lists (EIP-2930)
​Nimaligi: Tranzaksiya qaysi manzillarga tegishini qat'iy belgilovchi xarita ro'yxati.
​Biz qanday ishlatamiz: Arbitraj yuborishimizdan oldin Go bot A birja Pair'i, B birja Pair'i va WBNB manzillarini shunga kiritadi. Bu orqali blokcheyn bizning tranzaksiyamizni osonroq hazm qiladi va komissiyamiz (gas xarajati) keskin tejaladi.
​29. Telemetry
​Nimaligi: Butun tizimning har bir qismi qancha vaqt (ms) olayotganini ko'rsatib turuvchi o'lchov asboblari paneli.
​Biz qanday ishlatamiz: A va B o'rtasida spred topilganidan boshlab simulyatsiya qilib o'q uzguncha Go bot qayerda kechikayotganini (bottlenecks) Prometheus va Grafana grafiklarida nazorat qilib, tizimni doimiy ravishda mukammallashtirib boramiz.



# BSC Arbitraj Botining To'liq Arxitektura Rejasi
 shu oqimni 6 ta asosiy bosqichga bo'lgan holda quramiz.
---
## Birinchi bosqich — Ko'z va quloq: Ma'lumot olish qatlami
Bu butun tizimning eng muhim bosqichi, chunki noto'g'ri yoki kechikkan ma'lumot = yo'qotilgan pul. Bu yerda to'rtta komponent birgalikda ishlaydi.
**Geth Noda** BSC tarmog'ining to'liq nusxasini o'z ichida saqlaydi. **IPC ulanishi** esa Go botimizga ushbu nodadan ma'lumotni websocket yoki HTTP orqali emas, balki to'g'ridan-to'g'ri operativ xotira orqali olish imkonini beradi — bu 50ms kechikishni 0ms ga tushiradi. **Pair Sync Eventlar** esa nodaga "A yoki B birjadagi har qanday narx o'zgarishida menga signal ber" deb buyruq beradi, shunda bot birjani har millisekundda so'rab o'tirmaydi. **Direct Peering** esa bizning nodamizni BSC validatorlariga geografik jihatdan eng yaqin joyga ulaydi, ya'ni signal dunyo bo'ylab aylanib kelmasdan to'g'ri keladigan bo'ladi.
Bu bosqichning natijasi: **RAM xotirasida doimiy yangilanib turuvchi jonli narx jadvali.**
---
## Ikkinchi bosqich — Elak: Filtrlash qatlami
Narx o'zgarishi signali keldi — lekin bu signal bizga keraklimi? BSC da soniyada minglab juftliklarning signali keladi, ularning 99%+ — vaqt va protsessor isrof. Bu yerda uchta komponent ketma-ket ishlaydi.
Avvalo, **RLP decode** xom bayt oqimini o'qilishi mumkin bo'lgan formatga o'giradi. Keyin **Hexadecimal kodlar** yordamida "bu tranzaksiya qaysi juftlikka tegishli?" degan savol javoblanadi. Va nihoyat, **Bloom Filter** bu juftlikni bizning **Whitelist** ro'yxatimiz bilan O(1) tezlikda — ya'ni qancha element bo'lishidan qat'i nazar, bir zumda — solishtiradi. Whitelist'da yo'q = darhol rad etish.
**ABI** esa shu bosqichda "yordamchi tarjimon" vazifasini o'taydi: hexadecimal kod nima demoqchiligini tushunarli ma'lumotga o'giradi, masalan "PancakeSwap'da 5000 USDT evaziga WBNB sotib olinyapti" degan xulosa chiqaradi.
Bu bosqichning natijasi: **Faqat Whitelist'dagi juftliklar bo'yicha, inson o'qiy oladigan formatdagi signal.**
---
## Uchinchi bosqich — Miya: Qaror qabul qilish qatlami
Mana bu yerda **Go bot** — loyihaning bosh "miyasi" — asosiy ishni bajaradi. Bu bosqich eng murakkabi, chunki bir vaqtda bir necha narsa sodir bo'ladi.
**Goroutines** yordamida Go bot bir vaqtda quyidagilarni parallel bajaradi: A birjaning signalini eshitish, B birjaning joriy narxini tahlil qilish, avvalgi simulyatsiya natijalarini saqlash. **RWMutex** esa bu parallel oqimlar bir-birining xotirasini buzmasligini ta'minlaydi — bu o'ta muhim, chunki xotira ziddiyati botni crash qildirishi mumkin.
Bot har bir signal uchun **foyda formulasini** real vaqtda hisoblaydi: `B_sotuv − A_xarid − Flashloan_foizi − Gaz_xarajati − Pora = Sof_foyda`. Bu formulada **WBNB** asosiy o'lchov birligi bo'lib xizmat qiladi. **Slippage** qiymati esa formulada "narx mening foydasiga o'zgarishi mumkin bo'lgan eng yomon holat" ni hisobga oladi — biz faqat eng yomon holatda ham foydali bo'lgan arbitrajlarnigina keyingi bosqichga o'tkazamiz.
Shu yerda **Hujum strategiyasi** ham ishlaydi: standard front-run logikasi o'rniga, maxfiy yo'nalish mantiq qo'llaniladi — bu botning raqiblardan asosiy farqi.
Bu bosqichning natijasi: **"Bu arbitraj foydali ko'rinadi" degan dastlabki qaror.**
---
## To'rtinchi bosqich — Virtual test: Simulyatsiya qatlami
Dastlabki qaror bor, lekin pulimizni xavf ostiga qo'yishdan oldin, biz uni virtual muhitda sinaymiz. Bu bosqich tizimning "sug'urta polisi" dir.
**In-Memory StateDB** — bu BSC blokcheynining hozirgi holatining to'liq nusxasi, Go bot xotirasida joylashgan. **Custom EVM (REVM)** esa standart EVM dan 10–50 marta tezroq ishlaydi, chunki Rust'da yozilgan va xavfsizlik cheklovlari olib tashlangan. Bu ikki komponent birgalikda **Local simulyatsiyani** amalga oshiradi: bot haqiqiy tarmoqqa birorta tranzaksiya yubormay turib, "agar men hozir bu arbitrajni qilsam, aniq nima bo'ladi?" degan savolga 1 ms ichida javob oladi.
Agar simulyatsiya natijasi musbat bo'lsa, biz haqiqiy tranzaksiyani yaratishga o'tamiz. Agar manfiy — signal o'chiriladi va bot keyingi signalni kutadi.
Bu bosqichning natijasi: **Aniq foyda raqami bilan tasdiqlangan, xavf baholangan qaror.**
---
## Beshinchi bosqich — Qo'l: Tranzaksiya yaratish va yuborish
Simulyatsiya o'tdi — endi haqiqiy tranzaksiya quriladi. Bu bosqich tezlik va arzonlikni bir vaqtda ta'minlashga yo'naltirilgan.
**Smartkontrakt** — bu botning BSC tarmog'idagi "vakili". Hamma amallar shu orqali bajariladi. Kontraktning ichida birinchi narsa **Flashloan** so'rovi: "menga 100,000$ miqdorida WBNB ber, men bir blok ichida qaytaraman." Keyin kontrakt A birjada xarid, B birjada sotuv, foydani o'zlashtirish, qarzni qaytarish operatsiyalarini ketma-ket bajaradi. Agar biror nuqtada foyda yo'qolsa, **Slippage** qulflovchi qoida ishga tushadi va hammasi **Revert** bo'ladi — faqat kichik gaz xarajati qoladi.
Kontrakt kodi **Yul (Assembly)** bilan optimallashtirilib yozilgan — bu birjalarning rasmiy Router'lariga murojaat qilish o'rniga, to'g'ridan-to'g'ri Pair kontraktlarining xotira manzillariga yozib, gaz xarajatini 20–40% kamaytiradi. **Access Lists (EIP-2930)** esa tranzaksiya qaysi manzillarni "tegib o'tishi" ni oldindan e'lon qilib, yana qo'shimcha gaz tejaydi. **EIP-1559** mexanizmi orqali optimal gaz narxi hisoblanadi. Agar parallel ikki arbitraj bir vaqtda tayyor bo'lsa, **Nonce menejmenti** ularni tartibli holda uzatishni ta'minlaydi.
Bu bosqichning natijasi: **Gaz jihatdan optimallashtirilgan, tayyor tranzaksiya.**
---
## Oltinchi bosqich — Qalqon va nayzа: Yetkazib berish va himoya qatlami
Tranzaksiya tayyor — lekin uni ommaga e'lon qilish = raqibga "men hozir arbitraj qilmoqchiman" deb aytish. Bu eng xavfli lahza.
**Private kanallar** (BloXroute va o'xshashi) orqali tranzaksiya umumiy Mempool'ni aylanib o'tib, to'g'ridan-to'g'ri validatorga yetkaziladi — **Qaroqchi botlar** ko'rolmaydi. **block.coinbase.transfer** esa validatorga foydaning bir qismini "pora" sifatida beradi, shunda validator bizning tranzaksiyamizni blokda birinchi o'ringa qo'yadi. Kontraktdagi **obfuskatsiya** esa kimdir kontraktni o'qishga urinsa, strategiyamizni tushunolmasligini ta'minlaydi.
Bu bosqichning natijasi: **Arbitraj tranzaksiyasi raqibsiz, birinchi bo'lib blokka kirdi.**
---
## Ettinchi bosqich — Ko'z: Monitoring
Bu bosqich qon aylanishining emas, balki **shifokorning** vazifasini o'taydi. **Telemetry** (Prometheus + Grafana) tizimning har bir bosqichi qancha vaqt olayotganini millisoniyada o'lchab ko'rsatadi. Masalan: "2-bosqich filtrlash 0.3ms, 4-bosqich simulyatsiya 1.2ms, 5-bosqich tranzaksiya yaratish 0.8ms." Bu grafiklar qayerda "tiqilib" qolayotganini ko'rsatib, qayerga kuch sarflash kerakligini aytadi.
---
## Yaxlit oqim xulosasi
Agar bularni bitta jumlada aytadigan bo'lsak:
> **Noda + IPC + Sync Events + Direct Peering** → signal keladi → **RLP + Hex + Bloom + Whitelist + ABI** → filtrlaydi → **Go Bot + Goroutines + Formula + Strategiya** → qaror qiladi → **StateDB + REVM + Simulyatsiya** → tasdiqlaydi → **Smartkontrakt + Flashloan + Yul + EIP-1559 + Nonce** → tranzaksiya quradi → **Private kanal + Pora + Obfuskatsiya** → xavfsiz yetkazadi → **Telemetry** → hamma narsani kuzatadi.
---

Avvalo bir muhim tamoyilni tushunib olaylik: Go'da papka = paket. Demak, internal/filter/ papkasidagi barcha fayllar filter paketiga tegishli bo'ladi va bir-birini erkin ko'ra oladi. Boshqa paketlar esa faqat siz "eksport" qilgan (bosh harf bilan boshlangan) narsalarni ko'ra oladi. Bu tabiiy "devor" arxitekturani tartibli saqlaydi.

arbitrage-bot/
│
├── cmd/
│            └── bot/
│                └── main.go
│
├── config/
│           ├── config.go
│           └── config.yaml
│
├── contracts/
│    ├── src/
│    │      ├── ArbitrageBot.sol
│    │      ├── FlashLoanReceiver.sol
│    │      └── interfaces/
│    │                        ├── IPancakePair.sol
│    │                        └── IWBNB.sol
│    └── abi/
│             └── ArbitrageBot.json
│
├── internal/
│   ├── node/
│   │     ├── geth.go
│   │     └── ipc.go
│   │
│   ├── listener/
│   │       ├── sync_event.go
│   │       ├── mempool.go
│   │       └── peering.go
│   │
│   ├── decoder/
│   │        ├── rlp.go
│   │        ├── hex.go
│   │        └── abi.go
│   │
│   ├── filter/
│   │       ├── bloom.go
│   │       └── whitelist.go
│   │
│   ├── pricing/
│   │    ├── calculator.go
│   │    └── slippage.go
│   │
│   ├── strategy/
│   │    ├── engine.go
│   │    └── secret.go
│   │
│   ├── simulation/
│   │      ├── statedb.go
│   │      ├── evm.go
│   │      └── runner.go
│   │
│   ├── executor/
│   │    ├── builder.go
│   │    ├── nonce.go
│   │    ├── gas.go
│   │    └── access_list.go
│   │
│   ├── contract/
│   │       ├── flashloan.go
│   │       ├── caller.go
│   │       └── coinbase.go
│   │
│   ├── transport/
│   │         ├── private_channel.go
│   │         └── broadcaster.go
│   │
│   ├── bot/
│   │        ├── bot.go
│   │        └── worker.go
│   │
│   └── telemetry/
│            ├── prometheus.go
│            └── grafana.go
│
├── pkg/
│         ├── types/
│         │            └── types.go
│         └── math/
│                         └── formula.go
│
├── go.mod
├── go.sum
└── README.md



Endi har bir papka va faylni nima uchun aynan shunday joylashtirganimizni tushuntirib o'taman.
cmd/bot/main.go — Tizimning "Yuragi"
Bu fayl hech qanday biznes logika yozmaydi. Uning yagona vazifasi — barcha qatlamlarni ishga tushirish va ularni bir-biriga ulash. Go'da bu "dependency injection" deb ataladi: har bir komponent o'ziga kerakli narsani tashqaridan oladi, o'zi qidirmaydi.
main.go quyidagi tartibda ishlaydi: config'ni yuklaydi → noda ulanishini ochadi → barcha listenerlarni ishga tushiradi → botni startlaydi → dastur to'xtatilguncha kutadi. Bu fayl 100 qatordan oshmasligi kerak — agar oshsa, demak biror narsa noto'g'ri joylashgan.
config/ — Butun tizimning sozlamalari
config.yaml faylida BSC RPC manzili, IPC socket yo'li, BloXroute API kaliti, whitelist token manzillari, gaz limiti, flashloan provayderi manzili va shu kabi barcha "o'zgaruvchi" parametrlar yoziladi. config.go esa shu YAML faylni o'qib, Go struct'lariga o'giradi.
Nima uchun alohida? Chunki konfiguratsiya o'zgarganda (masalan, yangi token whitelist'ga qo'shilganda) hech qanday Go kodi qayta yozilmaydi — faqat YAML fayl yangilanadi.
contracts/ — Solidity va ABI
Bu papka Go kodi emas, Solidity kodlari uchun. src/ ichida haqiqiy kontrakt manbalari yotadi. abi/ ichida esa Solidity kompilyatsiya qilingandan so'ng hosil bo'lgan JSON fayl — Go botimiz aynan shu JSON orqali kontraktga qo'ng'iroq qiladi.
ArbitrageBot.sol — bu botning BSC dagi "vakili". Uning ichida Yul optimizatsiyalari, slippage qulfi, revert mexanizmi va block.coinbase.transfer kodi bo'ladi. FlashLoanReceiver.sol esa flashloan protokoli (masalan, PancakeSwap v3) ga javob beruvchi callback funksiyani o'z ichiga oladi.
internal/node/ — Geth va IPC (1-qatlam boshi)
geth.go Geth noda instansiyasiga ulanishni boshqaradi. U nodaning tirik yoki o'lik ekanini tekshiradi, ulanish uzilsa qayta ulanadi. ipc.go esa aynan IPC socket orqali (geth.ipc fayli) Go botni nodaga ulaydi — bu websocket yoki HTTP dan farqli o'laroq, xotiradan xotiraga to'g'ridan-to'g'ri gapiradi va kechikish amalda nolga teng bo'ladi.
internal/listener/ — Signal qabul qilish (1-qatlam)
sync_event.go — bu fayl Pair kontraktlaridan keladigan Sync(reserve0, reserve1) eventlarini tinglaydi. Har qanday narx o'zgarganda bu event otiladi va bizning RAM xotiradagi narx jadvali yangilanadi. Bu "so'rov-javob" modelidan ko'ra ancha samaraliroq — bot o'zi emas, tarmoq botga xabar beradi.
mempool.go — hali blokka kirmagan, "uchib yurgan" tranzaksiyalarni ushlaydi. Nima uchun? Chunki kimdir A birjada katta xarid qilmoqchi bo'lsa, bu narxni ko'taradi — biz esa o'sha tranzaksiya blokka kirishidan oldin arbitrajni boshlashimiz mumkin.
peering.go — Direct Peering sozlamalarini boshqaradi. Bu papkadagi kod nodamizning BSC validatorlariga qanchalik "yaqin" ekanini belgilaydi.
internal/decoder/ — Xom ma'lumotni o'qish (2-qatlam boshi)
rlp.go — mempool'dan keladigan xom bayt oqimini ochadi. Blokcheyndagi barcha tranzaksiyalar RLP formatida "qadoqlangan" keladi, bu fayl o'sha qadoqni ochadi.
hex.go — ochilgan ma'lumotdan "qaysi funksiya chaqirilmoqda, qaysi manzilga, qancha miqdor" degan savolga javob beradi. Hexadecimal function selector'larni tahlil qiladi.
abi.go — eng yuqori darajali decoder. U hex.go natijasini olib, ABI lug'ati yordamida "PancakeSwap Router'ining swapExactTokensForTokens funksiyasi chaqirilmoqda, 5000 USDT berib WBNB olmoqchi" degan aniq, tushunarli ma'lumotga aylantiradi.
internal/filter/ — Elak (2-qatlam)
bloom.go — matematik elak. Decoder'dan chiqqan manzilni oladi va "bu manzil bizning whitelist'imizda bormi?" degan savolga O(1) tezlikda javob beradi. Minglab tokenlar bo'lsa ham javob tezligi o'zgarmaydi.
whitelist.go — ishonchli juftliklar ro'yxatini boshqaradi. Bu faqat ro'yxat emas, balki har bir juftlik haqida qo'shimcha ma'lumot ham saqlaydi: minimal likvidlik chegarasi, maksimal slippage, honeypot emasligini tasdiqlagan sana va hokazo.
internal/pricing/ — Raqamlar hisob-kitobi
calculator.go — foyda formulasining Go implementatsiyasi. U A birja rezervlarini, B birja rezervlarini, flashloan foizini, taxminiy gaz xarajatini va pora miqdorini olib, aniq sof foyda raqamini qaytaradi. Bu fayl toza matematika — hech qanday tarmoq muloqoti yo'q.
slippage.go — narx sirpanishini hisoblaydi. Biz 100,000$ lik WBNB sotib olmoqchimiz — lekin bu katta miqdor o'zi ham narxni ko'taradi (price impact). Slippage.go aynan shu "o'z ta'sirimizni" hisobga oladi.
internal/strategy/ — Qaror qabul qilish miyasi
engine.go — barcha ma'lumotlarni olib, "arbitraj qilamizmi yoki yo'qmi?" degan yakuniy savolga javob beradi. U pricing, slippage, raqobatchilar faolligi va joriy tarmoq holati asosida qaror qabul qiladi.
secret.go — bu loyihaning eng qimmatli fayli. Bu yerda sizning maxfiy yo'nalish mantig'ingiz yashaydi. Standart front-run yoki sandwich shablonlari emas, balki sizning o'zingizning algoritimingiz. Bu fayl .gitignore'ga qo'shilishi va hech qachon ommaviy repozitoriyga chiqmasligi kerak.
internal/simulation/ — Virtual test poligoni (4-qatlam)
statedb.go — BSC blokcheynining joriy holatini RAM xotirasida saqlaydi. Har bir Sync event kelganda bu "virtual blokcheyn" ham yangilanib turadi.
evm.go — Custom EVM (REVM) bilan integratsiya. Rust'da yozilgan REVM kutubxonasini Go'dan CGo yoki subprocess orqali chaqiradi.
runner.go — simulyatsiyani boshqaruvchi asosiy fayl. U strategy'dan "arbitraj qil" buyrug'ini oladi, statedb va evm yordamida virtual muhitda o'tkazadi va aniq natija qaytaradi: "muvaffaqiyatli, sof foyda 0.003 WBNB" yoki "revert, sabab: slippage limitdan oshdi".
internal/executor/ — Tranzaksiya zavodi (5-qatlam)
builder.go — simulyatsiya o'tgandan so'ng haqiqiy tranzaksiya ob'ektini quradi. U kontrakt manzilini, calldata'ni, gaz limitini va boshqa parametrlarni birlashtirib, imzolashga tayyor tranzaksiya qaytaradi.
nonce.go — parallel arbitrajlar uchun nonce tartibini boshqaradi. Agar bir vaqtda ikkita imkoniyat chiqsa, nonce konflikt qilmasligi uchun bu fayl markaziy "navbat registri" vazifasini o'taydi.
gas.go — EIP-1559 mexanizmi asosida optimal baseFee va priorityFee hisoblaydi. Haddan oshiq gaz = foyda kamayadi, kam gaz = tranzaksiya o'tmaydi.
access_list.go — tranzaksiyaga EIP-2930 access list qo'shadi. Bu "men bu tranzaksiyada faqat mana bu manzillarni ishlataman" deb validatorga oldindan aytish — gaz xarajatini 10–15% tejaydi.
internal/contract/ — Smartkontrakt bilan muloqot
flashloan.go — flashloan so'rovini shakllantiradi. Qaysi provayderdan (PancakeSwap v3, AAVE BSC), qancha miqdorda, qaysi token uchun so'ralishini boshqaradi.
caller.go — Go bot tomonidan smartkontraktga yuboriluvchi calldata'ni encode qiladi. Kontrakt funksiyalarini ABI orqali chaqiradi.
coinbase.go — validatorga pora miqdorini hisoblaydi va block.coinbase.transfer chaqiruvini tayyorlaydi. Pora miqdori dinamik bo'lishi kerak: foyda katta bo'lsa pora ko'proq beriladi, shunda blokda birinchi o'ringa chiqish ehtimoli ortadi.
internal/transport/ — Xavfsiz yetkazish (6-qatlam)
private_channel.go — BloXroute yoki o'xshash xizmatlar bilan integratsiya. Tayyor tranzaksiyani umumiy Mempool'ga emas, bevosita shu kanal orqali validatorlarga yuboradi.
broadcaster.go — yuborish mantiqini boshqaradi: asosiy kanal ishlamay qolsa, fallback strategiyasi qanday bo'lishini belgilaydi.
internal/bot/ — Hammasini birlashtiruvchi markaz
bot.go — barcha qatlamlarni birlashtirib, asosiy tsiklni yuritadi. U listenerdan signal oladi, decoder va filter orqali o'tkazadi, strategy qaror qiladi, simulation tasdiqlaydi, executor tranzaksiya quradi, transport yuboradi.
worker.go — Goroutines va RWMutex boshqaruvi shu yerda. Har bir signal alohida goroutine'da qayta ishlanadi, lekin umumiy ma'lumot (narx jadvali, nonce) ga kirishda mutex qulflaydi.
internal/telemetry/ — Kuzatuv paneli
prometheus.go — har bir bosqich qancha vaqt olayotgani, nechta signal keldi, nechta simulyatsiya o'tdi/o'tmadi, nechta tranzaksiya yuborildi kabi metrikalarni Prometheus'ga eksport qiladi.
grafana.go — Grafana dashboard konfiguratsiyasini boshqaradi yoki tayyor JSON konfiguratsiyasini saqlaydi.
pkg/ — Umumiy kutubxona
pkg/types/types.go — barcha paketlar ishlatadigan umumiy ma'lumot turlari shu yerda: ArbitrageOpportunity, PairData, SimulationResult, Transaction va hokazo structlar. Bu faylni barcha paketlar import qiladi, shuning uchun u internal/ ichida emas, pkg/ ichida turadi.
pkg/math/formula.go — sof matematik funksiyalar: big.Int arifmetikasi, foiz hisoblash, wei/ether konvertatsiya va hokazo.
Qaysi tartibda qurish kerak?
Eng muhim savol — boshlash tartibi. Men quyidagi ketma-ketlikni tavsiya qilaman, chunki har bir qadam keyingisini test qilishga imkon beradi.
Birinchi navbatda config/ va pkg/types/ quriladi — bular asosdir, barchasi ularga bog'liq. Keyin internal/node/ va internal/listener/ — ma'lumot oqimini ishga tushirasiz. Undan keyin internal/decoder/ va internal/filter/ — signallar to'g'ri kelyaptimi, filter to'g'ri ishlayaptimi tekshirasiz. So'ngra internal/simulation/ — bu qatlam tayyor bo'lmay turib hech qanday real pul xavf ostiga qo'yilmasligi kerak. Faqat shundan keyin internal/executor/ va internal/contract/ va oxirida internal/transport/ quriladi.
internal/telemetry/ esa har bir qatlam bilan parallel qurilishi kerak — har bir yangi komponent yozilganda uning metrikasi ham qo'shiladi. Aks holda monitoring keyinga surilib, umuman qurilmay qoladi.
