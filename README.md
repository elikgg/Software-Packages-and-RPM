# Software-Packages-and-RPM
📦 RPM nədir?
RPM (RPM Package Manager) — Red Hat tərəfindən hazırlanmış proqram təminatını paketləmə və yayma sistemi üçün standartlaşdırılmış formatdır. Bu sistemin əsas üstünlükləri:

Proqramların sistemə necə quraşdırıldığını və silindiyini izləməyə imkan verir.

Asılılıqları yoxlayır və zəruri komponentlərin olub olmadığını təsdiqləyir.

Lokal RPM verilənlər bazasında quraşdırılmış paketlər haqqında məlumat saxlanılır.

Red Hat Enterprise Linux (RHEL) üçün bütün proqram təminatları RPM şəklində təqdim olunur.

🧱 RPM paket fayl adının strukturu
RPM fayl adları dörd əsas hissədən ibarətdir və .rpm ilə bitir:

Ad — paketdə olan proqramı bildirir. Məsələn, coreutils.

Versiya — proqramın versiya nömrəsi. Məsələn, 8.32.

Buraxılış — paketləyicinin təyin etdiyi buraxılış nömrəsi. Məsələn, 31.el9.

Arxitektura — hansı prosessor arxitekturası üçün uyğun olduğunu göstərir. Məsələn, x86_64 — 64-bit x86 üçün, aarch64 — ARM üçün.

📥 RPM paketlərinin əldə edilməsi və quraşdırılması
RPM paketləri çox zaman internet üzərindən repozitoriyalardan yüklənir. Repozitoriya — proqram paketlərinin saxlandığı mərkəzləşdirilmiş yerdir.

RPM meneceri aşağıdakı qaydada davranır:

Əgər bir paketdən bir neçə versiya varsa, ən yeni versiya seçilir.

Eyni versiyanın bir neçə buraxılışı varsa, yenisi seçilərək quraşdırılır.

🗂️ RPM paketinin tərkibi
Hər bir RPM paketi bu komponentləri özündə birləşdirir:

Sistemə quraşdırılacaq proqram faylları.

Metaməlumat: paket adı, versiyası, buraxılışı, arxitekturası, qısa izahat, asılılıqlar, lisenziya, dəyişiklik qeydləri və s.

Quraşdırma, yeniləmə və silmə zamanı avtomatik icra olunan skriptlər.

🔐 Rəqəmsal imzalama
RPM paketləri, adətən, GPG (GNU Privacy Guard) açarları ilə imzalanır. Red Hat bütün təqdim etdiyi paketləri rəqəmsal olaraq imzalayır. Quraşdırma zamanı RPM sistemi imzanı yoxlayır, əgər uyğun deyilsə, paket quraşdırılmır.

🔄 RPM vasitəsilə proqram yeniləmələri
Red Hat hər yeniləmə üçün tam bir RPM paketi təqdim edir. Sistemə əvvəlki versiyanı quraşdırmağa ehtiyac yoxdur.

Yeniləmə prosesi belə işləyir:

Əvvəlki versiya silinir.

Yeni versiya quraşdırılır.

Konfiqurasiya faylları qorunur (lakin bu paketləyici tərəfindən təyin olunur).

Əgər paket konflikt yaratmayan fayl adları ilə tərtib olunubsa, birdən çox versiya quraşdırıla bilər. Məsələn, kernel paketləri eyni anda bir neçə versiyada sistemdə mövcud ola bilər.

🛠️ RPM paketinin quraşdırılması prosesi
Əgər podman adlı paketin .rpm faylını lokal kataloquna yükləmisənsə, onu sistemə quraşdırmaq üçün aşağıdakı addımlar yerinə yetirilir:

RPM paketi yoxlanılır.

Quraşdırma üçün hazırlanma prosesi başlayır.

Fayllar sistemə əlavə olunur və quraşdırma tamamlanır.

⚠️ Təhlükəsizlik xəbərdarlığı
Üçüncü tərəf paketlərini quraşdırarkən diqqətli olmaq lazımdır. RPM faylında root səlahiyyətləri ilə işləyən skriptlər ola bilər. Bu, potensial təhlükə yarada bilər.

📤 RPM paketindən faylların çıxarılması (extract)
Əgər RPM faylını sistemə quraşdırmadan onun içindəki faylları görmək və ya çıxarmaq istəyirsənsə, aşağıdakı mərhələlər yerinə yetirilir:

RPM faylı rpm2cpio vasitəsilə cpio arxivinə çevrilir.

Daha sonra cpio vasitəsilə fayllar çıxarılır.

🧾 Misal: Faylların çıxarılması
Paket adı: httpd-2.4.51-7.el9_0.x86_64.rpm

Bu paketdən aşağıdakı fayllar çıxarıla bilər:

./etc/httpd/conf/

./etc/httpd/conf.d/autoindex.conf

./etc/httpd/conf.d/userdir.conf

./etc/httpd/conf.d/welcome.conf

./etc/httpd/conf.modules.d/00-base.conf

./etc/httpd/conf.modules.d/00-dav.conf

./etc/httpd/conf.modules.d/00-mpm.conf

./etc/httpd/conf.modules.d/00-optional.conf

./etc/httpd/conf.modules.d/00-proxy.conf

./etc/httpd/conf.modules.d/01-cgi.conf

./etc/httpd/conf.modules.d/README

./etc/httpd/conf/httpd.conf

Bu fayllar sistemdə eyni strukturda çıxarılır.

🔍 Yalnız bir faylı çıxarmaq
Əgər yalnız httpd.conf adlı konfiqurasiya faylını çıxarmaq istəyirsənsə, həmin faylın yolunu göstərərək onu çıxarmaq mümkündür.

Fayl çıxarıldıqdan sonra etc/httpd/conf/ içində yerləşəcək.

📄 Paketin içindəki faylların siyahısını çıxarmaq
RPM faylındakı bütün faylların siyahısını çıxarmaq və onların ölçüsü, icazələri və modifikasiya tarixi haqqında məlumat almaq olar. Bu, xüsusilə təhlil məqsədi ilə faydalıdır.

Məsələn, httpd.conf, README, 00-base.conf kimi faylların sistemdə haraya quraşdırılacağını bu yolla əvvəlcədən görə bilərsən.

✅ Nəticə
RPM sistemi Linux mühitində güclü, təhlükəsiz və çevik paket idarəetmə vasitəsidir. O, sistem administratorlarına proqram təminatının qurulması, yenilənməsi, silinməsi və yoxlanması üçün əlverişli imkanlar təqdim edir.

RPM paketlərini effektiv şəkildə istifadə etməklə sən:

Quraşdırmaları izləyə bilərsən;

Təhlükəli skriptlərdən xəbərdar ola bilərsən;

Sistemini daha stabil və nəzarət edilə bilən şəkildə idarə edə bilərsən.
