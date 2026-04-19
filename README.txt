# Marangoz Oyunu — Carpenter Game

Unreal Engine 5.7 ile geliştirilmiş çok oyunculu (4 kişi) bir iş birliği oyunu.

## Nasıl Açılır

1. ZIP'i çıkart
2. `CaseStudy.uproject` dosyasına çift tıkla
3. UE5.7 ile aç
4. Play tuşuna bas → Net Mode: **Listen Server**, Players: **4**

## Oynanış

- Oyuncular ortak bütçe ile başlar
- Sayaçta rastgele sipariş belirir
- Oyşma makinesinde obje üretilir
- Boya tezgahında doğru renge boyanır
- Sipariş alanına bırakılarak teslim edilir
- Döngü devam eder

## Ödeme Sistemi

| Durum | Ödeme |

| Doğru obje + doğru renk | Tam ödeme |
| Doğru obje + yanlış renk | %50 ödeme |
| Yanlış obje | 0 ödeme |

## Teknik Yapı

- **Blueprint** tabanlı geliştirme
- **GameState** — paylaşımlı bütçe ve sipariş verisi (Replicated)
- **GameMode** — sipariş oluşturma ve teslimat mantığı (sadece server)
- **Server RPC** — tüm oyun aksiyonları server üzerinden doğrulanır
- **RepNotify** — renk, bütçe ve sipariş değişimleri tüm oyunculara anlık yansır
- **BPI_Interactable** — ortak etkileşim arayüzü (Interface pattern)
- **E_PaintColor** — renk yönetimi için Enum (Single Source of Truth)

## Kontroller

| Tuş | Eylem |

| E | Obje al / bırak / etkileş |