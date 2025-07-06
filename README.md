[![MseeP.ai Security Assessment Badge](https://mseep.net/pr/tnhann-animalsapp-badge.png)](https://mseep.ai/app/tnhann-animalsapp)

# 🐾 Animal Nutrition API & MCP Server + Mobil Uygulama

Hayvanların beslenme alışkanlıkları hakkında detaylı bilgi sağlayan çok amaçlı servis. Web API, MCP server ve mobil uygulama desteği sunar.

**🚀 Smithery MCP Server:** `https://smithery.ai/server/@Tnhann/animalsapp`

## 🌟 Özellikler

- **API Ninjas Integration**: Hayvan bilgilerini API Ninjas Animals API'den alır
- **Gemini AI Integration**: Google Gemini AI kullanarak beslenme alışkanlıklarını analiz eder
- **Türkçe Destek**: Türkçe hayvan isimleri ve açıklamalar
- **Detaylı Bilgi**: 3-5 besin örneği ve beslenme türü (etçil, otçul, hepçil) bilgisi
- **Web Interface**: Kullanıcı dostu web arayüzü
- **REST API**: HTTP GET endpoint'i
- **MCP Uyumlu**: Model Context Protocol standardına uygun
- **📱 Mobil Uygulama**: Expo Go ile çalışan React Native uygulaması
  - 💬 WhatsApp benzeri sohbet arayüzü
  - 🌈 Hamburger menü sistemi (tab bar yerine)
  - ⌨️ Klavye uyumlu tasarım
  - 🐾 Hayvan kategorileri
- **🚀 Smithery MCP Server**: Production-ready MCP server deployment

## 🚀 Kurulum

1. **Bağımlılıkları yükleyin:**
```bash
npm install
```

2. **API Anahtarları:**
   - API anahtarlarınızı `.env` dosyasına ekleyin:

```
# .env dosyası
API_NINJAS_KEY=your_api_ninjas_key
GEMINI_API_KEY=your_gemini_api_key
SMITHERY_API_KEY=your_smithery_api_key
```

## 🔧 Kullanım

### 🌐 Web Interface (Önerilen)

```bash
npm run api-server
```

Tarayıcınızda `http://localhost:3000` adresini açın. Güzel bir web arayüzü ile hayvan beslenme bilgilerini sorgulayabilirsiniz.

### 🔌 Smithery MCP Server (YENİ!)

**Server URL:** `https://smithery.ai/server/@Tnhann/animalsapp`

**Mevcut Tools:**
- `get_animal_nutrition` - Hayvan beslenme bilgileri
- `get_animal_info` - API Ninjas hayvan bilgileri

**Claude Desktop ile Kullanım:**
1. Claude Desktop'ta Settings > MCP Servers
2. Add Server: `https://smithery.ai/server/@Tnhann/animalsapp`
3. API Key: API anahtarınızı .env dosyasından alın
4. Tools'u aktifleştirin

**Örnek Kullanım:**
```
Claude'a şunu sorun: "get_animal_nutrition tool'unu kullanarak aslan hakkında beslenme bilgisi al"
```

### 📱 Mobil Uygulama

```bash
cd mobile-app
npm install
npm start
```

Expo Go uygulaması ile QR kodu tarayarak mobil uygulamayı kullanabilirsiniz.

**Mobil Uygulama Özellikleri:**
- 💬 WhatsApp benzeri chat arayüzü
- 🚀 Hızlı soru butonları
- 📱 iOS ve Android desteği
- 🔄 Gerçek zamanlı API iletişimi
- 🌈 Tab bar yerine hamburger menü sistemi
- ⌨️ Klavye açıldığında mesajların görünmesini sağlayan geliştirmeler

### 🚀 Local MCP Server

```bash
npm run mcp-server
```

Local MCP server'ı başlatır. Claude Desktop veya diğer MCP client'lar ile kullanabilirsiniz.

### 📊 Demo Çalıştırma

```bash
npm run demo
```

Bu komut 5 farklı hayvan (aslan, fil, kartal, köpek, kedi) için beslenme bilgilerini gösterir.

### 🧪 Test Etme

```bash
npm run test-nutrition
```

## 📋 API Kullanımı

### REST API Endpoint

**GET** `/animal-nutrition?animal={hayvan_adı}`

**Örnek (Local):**
```bash
curl "http://localhost:3000/animal-nutrition?animal=aslan"
```

### Smithery MCP Tools

#### 1. get_animal_nutrition

**Açıklama:** Hayvanların beslenme alışkanlıkları hakkında detaylı bilgi alın.

**Parametreler:**
```json
{
  "animalName": "string" // Türkçe veya İngilizce hayvan adı
}
```

**Örnek:**
```json
{
  "name": "get_animal_nutrition",
  "arguments": {
    "animalName": "aslan"
  }
}
```

#### 2. get_animal_info

**Açıklama:** API Ninjas'dan hayvan bilgilerini alır.

**Parametreler:**
```json
{
  "name": "string" // İngilizce hayvan adı
}
```

**Örnek:**
```json
{
  "name": "get_animal_info", 
  "arguments": {
    "name": "lion"
  }
}
```

## 🛠️ Teknik Detaylar

### Kullanılan Teknolojiler

- **Node.js**: Runtime environment
- **TypeScript**: Type-safe development
- **Google GenAI SDK**: Gemini AI integration
- **API Ninjas**: Animal data source
- **MCP SDK**: Model Context Protocol implementation
- **Native HTTP**: Lightweight web server
- **React Native**: Mobil uygulama framework
- **Expo**: Mobil geliştirme platformu
- **Smithery**: MCP server hosting platform

### Proje Yapısı

```
AnimalApp/
├── src/
│   ├── mastra/
│   │   ├── tools/
│   │   │   └── animal-nutrition.ts    # API tools
│   │   └── index.ts                   # Mastra configuration
│   ├── api-server.ts                  # HTTP API server
│   ├── mcp-server.ts                  # MCP server implementation
│   ├── demo.ts                        # Demo script
│   └── test-animal-nutrition.ts       # Test file
├── public/
│   └── index.html                     # Web interface
├── mobile-app/                        # 📱 Mobil uygulama
│   ├── App.js                         # Ana mobil uygulama
│   ├── screens/                       # Ekranlar klasörü
│   │   ├── home/                      # Ana sayfa/chat ekranı
│   │   ├── search/                    # Arama ekranı  
│   │   ├── favorites/                 # Favoriler ekranı
│   │   ├── details/                   # Hayvan detay ekranı
│   │   └── splash/                    # Açılış ekranı
│   ├── package.json                   # Mobil bağımlılıklar
│   └── README.md                      # Mobil uygulama kılavuzu
├── .smithery/                         # 🚀 Smithery config
│   ├── config.json                    # Smithery konfigürasyonu
│   ├── mcp-config.json               # MCP server konfigürasyonu
│   └── deploy.yml                     # Deployment workflow
├── .env.example                       # Örnek çevre değişkenleri
├── smithery.json                      # Smithery deployment config
├── smithery.yaml                      # Smithery MCP config
├── package.json
└── README.md
```

## 🔍 Örnekler

### Smithery MCP Server Kullanımı

1. **Claude Desktop'ta:**
   - Settings > MCP Servers
   - Add: `https://smithery.ai/server/@Tnhann/animalsapp`
   - API Key: API anahtarınızı .env dosyasından alın

2. **Cursor'da:**
   - Extensions > MCP
   - Add Server: `@Tnhann/animalsapp`

3. **VS Code'da:**
   - MCP Extension yükleyin
   - Server ekleyin: `https://smithery.ai/server/@Tnhann/animalsapp`

### Web Interface

1. `npm run api-server` ile server'ı başlatın
2. `http://localhost:3000` adresini açın
3. Hayvan adını girin veya örneklerden birini seçin
4. Sonuçları görüntüleyin

### Mobil Uygulama

1. `cd mobile-app && npm install` ile bağımlılıkları yükleyin
2. `.env.example` dosyasını `.env` olarak kopyalayıp API URL'i güncelleyin
3. `npm start` ile Expo dev server'ı başlatın
4. Expo Go ile QR kodu tarayın
5. Chat arayüzünde hayvan sorularınızı sorun

### Demo Çalıştırma

```bash
npm run demo
```

Bu komut şu hayvanlar için beslenme bilgilerini gösterir:
- 🦁 Aslan
- 🐘 Fil  
- 🦅 Kartal
- 🐕 Köpek
- 🐱 Kedi

### REST API Kullanımı

```bash
# Local development
curl "http://localhost:3000/animal-nutrition?animal=aslan"
curl "http://localhost:3000/health"
```

### MCP Client ile Kullanım

**Local MCP Server:**
1. Server'ı başlatın: `npm run mcp-server`
2. MCP client'ınızda tools'u kullanın

**Smithery MCP Server:**
1. URL: `https://smithery.ai/server/@Tnhann/animalsapp`
2. API Key: `.env` dosyasından alın
3. Tools: `get_animal_nutrition`, `get_animal_info`

## 🎯 Desteklenen Hayvanlar

Sistem herhangi bir hayvan adını kabul eder. Örnekler:
- **Türkçe**: aslan, kaplan, fil, kartal, köpek, kedi, balık, yılan, vb.
- **İngilizce**: lion, tiger, elephant, eagle, dog, cat, fish, snake, vb.

## 📜 Mevcut Script'ler

```bash
# Development
npm run api-server      # Web interface + REST API
npm run mcp-server      # Local MCP server
npm run mcp             # Local MCP server (alias)
npm run demo           # Demo çalıştırma
npm run test-nutrition # Test etme
npm run dev            # Mastra development
npm run build          # Mastra build

# Smithery Deployment
npm run smithery:deploy    # Deploy to Smithery
npm run smithery:mcp       # Deploy MCP server
npm run smithery:status    # Check deployment status
npm run smithery:logs      # View real-time logs
npm run smithery:rollback  # Rollback to previous version

# Mobil uygulama (mobile-app/ dizininde)
cd mobile-app
npm start              # Expo dev server
npm run android        # Android emulator
npm run ios            # iOS simulator
```

## 📱 Mobil Uygulama Kurulumu

1. **Expo CLI yükleyin:**
```bash
npm install -g expo-cli
```

2. **Mobil uygulamayı başlatın:**
```bash
cd mobile-app
npm install
npm start
```

3. **API Url'i ayarlayın:**
```
# mobile-app/.env dosyasında
API_URL=https://your-api-url.com
```

## 🌐 Deployment Seçenekleri

1. **Smithery MCP (Önerilen)**: Production-ready MCP server
2. **Railway**: Hızlı deployment
3. **Vercel**: Serverless deployment
4. **Heroku**: Geleneksel PaaS
5. **Docker**: Container deployment

Detaylı deployment talimatları için `DEPLOYMENT.md` dosyasına bakın.

## 🔧 Environment Variables

```env
# .env dosyası - API anahtarlarınızı buraya ekleyin (Github'a push etmeyin!)
NODE_ENV=production
PORT=3000
SMITHERY_API_KEY=your_smithery_api_key
API_NINJAS_KEY=your_api_ninjas_key
GEMINI_API_KEY=your_gemini_api_key
```

## 📊 Monitoring & Analytics

Smithery dashboard'da şunları izleyebilirsiniz:
- MCP tool usage metrikleri
- Request/Response times
- Error rates ve success rates
- API call statistics
- Real-time logs

## 🔗 Bağlantılar

- **Smithery MCP Server**: https://smithery.ai/server/@Tnhann/animalsapp
- **API Ninjas**: https://api-ninjas.com
- **Google Gemini AI**: https://ai.google.dev
- **Model Context Protocol**: https://modelcontextprotocol.io
- **Smithery Platform**: https://smithery.ai 