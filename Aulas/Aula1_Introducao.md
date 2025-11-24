   # Aula 1: Introdução


---

##  Links Importantes
- **Link da Aula 1:** [https://www.canva.com/design/DAGojCv1lmA/G5JgXoBpsi_ZpL2GA-tiZg/edit?utm_content=DAGojCv1lmA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton](https://www.canva.com/design/DAGoNK0TSbQ/n3H4YVsCdqZoMLS-KI0qZw/edit?utm_content=DAGoNK0TSbQ&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)
- **Documentação Oficial:** https://reactnative.dev/  
- **Projeto da Aula:** https://github.com/DalvanaRibeiro/UC15_241N_ComponentesPrincipais  


---

##  Por que o React Native existe?  
Antes de pensarmos em código, precisamos entender **o motivo do nascimento do React Native**.

Em 2013, o Facebook enfrentava um grande problema:  
- A versão mobile do Facebook era **lenta**,  
- O time precisava **desenvolver duas vezes** (Android e iOS separadamente),  
- As atualizações demoravam para chegar ao usuário.

O time já usava React na Web e queria trazer a **mesma filosofia** para o mundo mobile:

> “E se pudéssemos escrever apps nativos usando JavaScript?”  
> — Ideia discutida no hackathon do Facebook que deu origem ao React Native.

Em 2015, o React Native foi oficialmente lançado.  
A promessa era **uma só base de código** entregando **interfaces nativas**, não webviews.

E funcionou.  
Hoje é usado por empresas como Meta, Instagram, Uber, Discord, Tesla, Shopify e milhares de times no mundo.

---

#  O que é o React Native?

React Native é um **framework JavaScript** que permite criar **aplicativos nativos** para Android e iOS usando:

- **JavaScript** (ou TypeScript)  
- **Componentes reutilizáveis**  
- **Estilo inspirado no CSS**  
- **Conceitos do React** (componentes, props, estados, hooks)

 Diferente de frameworks híbridos, o React Native **renderiza componentes realmente nativos**, como `<View>`, `<Text>`, `<Image>`.

Isso garante:
- Alta performance  
- Aparência nativa  
- Experiência fluida  

---

# ⚙️ Como o React Native funciona?

React Native utiliza uma arquitetura simples:

| Parte | O que faz |
|------|-----------|
| **JavaScript Thread** | Onde seu código React roda |
| **Bridge** | Ponte de comunicação |
| **Native Layer** (Android/iOS) | Onde vivem os componentes nativos |

 O JavaScript envia comandos → a camada nativa cria botões, textos, imagens etc.

---

#  O que é o Expo e o Expo Go?

##  Expo
Expo é um **ecossistema** que facilita criar aplicações React Native sem configuração pesada em Android Studio ou Xcode.

Ele oferece:
- Build simplificada  
- Sistema de plugins  
- Suporte a sensores  
- CLI poderosa  
- Servidor de desenvolvimento rápido  

##  Expo Go
É um **app disponível na Play Store e App Store**.

Ele permite rodar seus apps **sem precisar compilar**.

Você escaneia um QR Code e pronto:
- O projeto abre no seu celular  
- Atualiza automaticamente  
- Testa tudo em segundos  

 Para primeira aula, o Expo Go é *perfeito*.

---

#  Como criamos o primeiro projeto

Com o comando **oficial e recomendado pela própria equipe Expo/React Native**:

```bash
npx create-expo-app@latest MeuPrimeiroApp
````

# Para executar: 

Entre na pasta do projeto:

````
cd MeuPrimeiroApp
````

e execute com o comando:

```` 
npx expo start
````

sempre dentro da pasta do projeto 😉.

---

Abraço

Prof. Dalvana Ribeiro




