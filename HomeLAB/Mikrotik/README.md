
# Dokumentacja techniczna sieci domowej opartej na Mikrotiku
Sercem sieci jest router brzegowy MikroTik hAP ax³, zarządzający odizolowanymi strefami VLAN (Zero Trust), bezpiecznym tunelem VPN oraz lokalnym serwerem druku CUPS uruchomionym w kontenerze Docker.

📂 Zawartość Repozytorium

W tym repozytorium znajdziesz pełną konfigurację oraz dokumentację mojego węzła sieciowego. Pliki zostały zanonimizowane pod kątem bezpieczeństwa (usunięto fizyczne adresy MAC, klucze prywatne oraz dane uwierzytelniające).


📄 Dokumentacja Techniczna Sieci.pdf

Pełne kompendium inżynierskie: opis architektury fizycznej i L2/L3, tabele IPAM, konfiguracja zapory sieciowej (Firewall) oraz profile CUPS.


⚙️ config-export.txt

Zanonimizowany, czysty i zweryfikowany eksport konfiguracji RouterOS v7 (.rsc) gotowy do analizy lub wdrożenia.


📜 skrypt-wifi_guest.txt

Skrypt administracyjny automatyzujący włączanie i wyłączanie wirtualnych interfejsów sieci gościnnej WiFi z logowaniem zdarzeń.


🎨 sys-banner.txt

Personalizowany, tekstowy baner powitalny ASCII wyświetlany podczas logowania do terminala SSH routera.


📐 Kluczowe Rozwiązania Architektoniczne

Segmentacja L2/L3 (VLAN Filtering): Sprzętowa izolacja stref sieciowych. Urządzenia IoT oraz sieć gościnna nie mają dostępu do sieci produkcyjnej LAN ani strefy zarządzania.

Stanowy Firewall (Default Drop): Restrykcyjna zapora sieciowa blokująca wszelki nieautoryzowany ruch międzystrefowy, z precyzyjnie zdefiniowanymi wyjątkami (np. integracja Home Assistant z LocalTuya).

Konteneryzacja lokalna (Docker on RouterOS): Izolowany serwer wydruku CUPS (tigerj/cups-airprint) uruchomiony w kontenerze bezpośrednio na MikroTiku, współdzielący drukarkę HP po protokole AppSocket (TCP 9100).

Zdalny Dostęp (WireGuard VPN): Szyfrowany tunel z optymalizacją wielkości pakietu (TCP MSS Clamping) dla bezpiecznej pracy zdalnej administratora.

Selektywny DNS (DHCP Option 6): Elastyczne przydzielanie lokalnego, filtrującego serwera DNS tylko dla zaufanych urządzeń roboczych.


