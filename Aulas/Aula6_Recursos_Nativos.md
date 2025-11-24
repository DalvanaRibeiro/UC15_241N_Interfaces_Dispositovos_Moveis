#   **Aula 6: Recursos Nativos no React Native (Expo)**  
## **Sensores, Câmera, Vibração, Localização, Haptics e Uso Real no Celular**

---



##  Links Importantes
 **Link da Aula 6:** https://www.canva.com/design/DAG5ojJ6jUA/5mXG54AMOJ8ebMtAENS_Lw/edit?utm_content=DAG5ojJ6jUA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
- **Documentação Expo Sensores:** https://docs.expo.dev/versions/latest/sdk/sensors/  
- **Expo Camera:** https://docs.expo.dev/versions/latest/sdk/camera/  
- **Expo Haptics:** https://docs.expo.dev/versions/latest/sdk/haptics/  
- **Expo Location:** https://docs.expo.dev/versions/latest/sdk/location/
- **Link do projeto:** https://github.com/DalvanaRibeiro/RecursosNativos_241N

---

# 1. O que são Recursos Nativos?

Recursos nativos são **funcionalidades reais do smartphone** que o app pode acessar, como:

📸 **Câmera**  
📍 **Localização (GPS)**  
🔊 **Microfone**  
📳 **Vibração / Haptics**  
🧭 **Acelerômetro / Giroscópio**  
🌡 **Barômetro**  
🎧 **Áudio**  
🗂 **Arquivos / Mídia**  

O React Native NÃO acessa esses recursos sozinho.  
Por isso usamos o **Expo**, que facilita tudo com apenas alguns imports.

---

# 2. Por que usar Recursos Nativos?

- Deixa o app **mais real e interativo**  
- Abre portas para projetos incríveis  
- Alunos entendem que um app é MUITO mais que telas  
- Permite criar:
  - Jogos simples  
  - Apps com vibração  
  - Leitor de QR Code  
  - Mapas  
  - Aplicativos fitness  
  - Câmera personalizada  
  - Gravação de voz  

---

# 3. Como instalar recursos nativos no Expo

Cada recurso tem sua própria biblioteca.

Exemplo para Câmera:
Câmera

````
npx expo install expo-camera
````
Localização (GPS)
````
npx expo install expo-location
````
Vibração / Haptics
````
npx expo install expo-haptics
````
Acelerômetro
````
npx expo install expo-sensors
````

# Quando usar cada recurso?

| Recurso       | Uso Ideal                         |
|---------------|-----------------------------------|
| **Câmera**     | Scan QR Code, tirar fotos, perfis |
| **Localização** | Mapas, rastreamento, clima        |
| **Acelerômetro** | Jogos, pedômetro                  |
| **Haptics**     | Feedback ao clicar                |
| **Microfone**   | Gravar áudio                      |
| **Barômetro**   | Apps de clima                     |
| **Vibração**    | Alertas, ações importantes        |

Abraços, 

Prof. Dalvana Ribeiro

