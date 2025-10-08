# 🧩 DW_ProductSync — SSIS ile Veri Senkronizasyonu Projesi

Bu proje, iki farklı SQL Server veritabanı (**ServerA** ve **ServerB**) arasındaki ürün verilerini karşılaştırıp farkları tespit ederek, sonuçları bir **Data Warehouse (DW)** tablosuna aktarmak için hazırlanmıştır.  
Tüm süreç **SQL Server Integration Services (SSIS)** kullanılarak tasarlanmıştır.

---

## 🎯 Proje Amacı

Farklı sistemlerde tutulan ürün bilgilerini otomatik olarak karşılaştırmak ve güncel durumu `DW_ProductSync` tablosuna yansıtarak:
- Yeni eklenen ürünleri,
- Güncellenen ürünleri,
- Silinen ürünleri  
tespit etmek.

---

## 🏗️ Süreç Adımları

### 1️⃣ **Clear DW_ProductSync Table**
Data Flow başlamadan önce, hedef tablo kontrol edilir:
```sql
IF OBJECT_ID('dbo.DW_ProductSync', 'U') IS NOT NULL
    TRUNCATE TABLE dbo.DW_ProductSync;
ELSE
    PRINT('Table not found – skipping truncate.');
