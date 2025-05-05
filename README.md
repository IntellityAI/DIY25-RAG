# Yapay Zeka RAG Sistemi

Bu proje, Yapay Zeka konusuyla ilgili dokümanlarını işleyerek bir Retrieval-Augmented Generation (RAG) sistemi oluşturmayı amaçlamaktadır. Proje, dokümanları yüklemek, bölümlere ayırmak, vektör temelli indekslemek, sorgulamak ve yapay zeka modeliyle yanıtlar üretmek için gerekli tüm adımları içerir.

## Proje Yapısı

```
.
├── .idea                         # IDE konfigürasyon dosyaları
├── data                          # Veri dosyaları
│   └── YapayZeka.pdf             # İşlenecek yapay zeka PDF belgesi
├── .env                          # Ortam değişkenleri (API anahtarları vb.)
├── requirements.txt              # Gerekli Python kütüphaneleri
└── RetrievalAugmentedGeneration.ipynb  # Ana notebook dosyası
```

## Özellikler

- **Doküman İşleme**: PDF dosyalarını yükleme ve ön işleme
- **Doküman Bölümleme**: Büyük metinleri anlamlı parçalara ayırma
- **Vektör İndeksleme**: Metin parçalarını OpenAI embeddings kullanarak vektörlere dönüştürme
- **Bilgi Getirme**: Sorguya en alakalı metin parçalarını bulma
- **Yanıt Üretme**: GPT-4o kullanarak bağlam-bilinçli yanıtlar oluşturma

## Kurulum

1. Projeyi zip dosyasından çıkarın.

2. Pycharm veya hangi IDE kullanıyorsanız çıkarılan dosyayı açın.

3. Gerekli kütüphaneleri yükleyin:
   ```
   pip install -r requirements.txt
   ```

## Kullanım

1. `RetrievalAugmentedGeneration.ipynb` dosyasını açın.

2. Notebook'taki hücreleri sırasıyla çalıştırın:
   - Doküman yükleme ve ön işleme
   - Doküman bölümleme
   - Vektör indeksleme ve kaydetme
   - Bilgi getirme ve sorgu testi
   - Yapay zeka ile yanıt üretme

## RAG Sistemi Nasıl Çalışır

1. **İndeksleme Aşaması**:
   - PDF dokümanı yüklenir ve metin ön işlemeye tabi tutulur
   - Doküman küçük parçalara bölünür (chunks)
   - Her bir parça için OpenAI embeddings kullanılarak vektör temsilleri oluşturulur
   - Vektörler FAISS indeksinde saklanır

2. **Sorgulama Aşaması**:
   - Kullanıcı sorusu vektör formuna dönüştürülür
   - Soru vektörüne en yakın doküman parçaları bulunur (semantik arama)
   - İlgili içerikler bağlam olarak kullanılır

3. **Yanıt Üretme Aşaması**:
   - Özel bir şablon kullanılarak GPT-4o'ya ilgili bağlam ve soru iletilir
   - Model, sağlanan bağlamı kullanarak Türkçe yanıt üretir
   - Yanıt en fazla 5 cümle ile sınırlandırılır

## Gereksinimler

- Python 3.8+
- langchain
- langchain-community
- langchain-core
- langchain-openai
- langchain-huggingface
- langchain-postgres
- python-dotenv
- faiss-cpu
- tiktoken
- pdfminer.six

## Not

Bu sistem şu anda Türkçe Yapay Zeka dokümanları için yapılandırılmıştır, ancak diğer dillerdeki ve konulardaki dokümanlar için de kolayca uyarlanabilir.