#   **Aula 4: Navegação Entre Telas com Expo Router**  
## **Rotas, Navegação, Pastas, Hooks e Funcionamento Didático**

---

##  Links Importantes
- **Documentação Oficial Expo Router:** https://expo.github.io/router/docs  
- **Link da Aula 4:** https://www.canva.com/design/DAGp43t159Q/p2QsZNForPG3lMRYoFw5sA/edit?utm_content=DAGp43t159Q&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton 
- **Projeto Base (banho e tosa):** https://github.com/DalvanaRibeiro/NavegacaoExpoRouterBanhoeTosa  


---

## 1. O que é o Expo Router?

O **Expo Router** é o sistema de navegação oficial do Expo, baseado em pastas.  
Ele funciona igual a sites:

📂 **Cada arquivo = uma tela**  
📁 **Cada pasta = um grupo de telas**

Isso deixa tudo simples e organizado.

---

 ## 2. Por que usar o Expo Router?

- Muito mais simples que React Navigation  
- Rápido  
- Baseado em arquivos  
- Sem configuração difícil  
- Navegação moderna  
- Perfeito para apps com muitas telas  

---
## 3. Como usar:

No terminal, dentro da pasta do projeto: 

````

npx expo install expo-router

````

Eventualmente se precisa ajustar o plugin no app.json:

````
{
  "expo": {
    "plugins": ["expo-router"],
    "experiments": {
      "typedRoutes": true
    }
  }
}



````

## 3. Estrutura básica de pastas

Quando criamos o projeto com Expo Router, a pasta fica assim:

<img width="387" height="410" alt="image" src="https://github.com/user-attachments/assets/b9e8d43f-57ed-410e-ac08-091eeb3e90ca" />


O que isso significa?

1. A pasta /app é o coração do Expo Router

No Expo Router, tudo que está dentro de /app vira uma rota.



O Expo Router funciona como um sistema de rotas baseado em arquivos, igual Next.js.

2. A pasta (tabs) indica um grupo de navegação em abas

O nome com parênteses — (tabs) — significa:

 “Isso é um grupo especial de rotas que será controlado por um layout.”

Ou seja:

Tudo dentro de (tabs) faz parte das tabs

Esse grupo tem uma navegação própria

Ele só funciona por causa do arquivo _layout.tsx
3. O arquivo (tabs)/_layout.tsx controla as abas

Esse arquivo é OBRIGATÓRIO dentro da pasta (tabs).

Ele informa ao Expo Router:

- quais telas serão abas
-  quais ícones/nomes terão
- qual tela abre primeiro dentro das tabs

Exemplo: 

``````
// Importa o Slot, que representa o local onde as telas serão carregadas
import { Slot } from "expo-router";

// Componente que envolve todo o aplicativo
export default function RootLayout() {
  // O Slot é onde cada tela (page) aparecerá
  return <Slot />;
}


``````

4. A pasta /screens dentro de (tabs) contém as telas das abas

Na imagem temos:

app/(tabs)/screens/
│   home.tsx
│   agendar.tsx
│   servicos.tsx
│   perfil.tsx


O Expo Router entende assim:
| Arquivo       | Rota dentro das tabs    |
| ------------- | ----------------------- |
| `home.tsx`    | `/home`                 |
| `agendar.tsx`  | `/agendar`               |
| `servicos.tsx`   | `/servicos`                |
| `perfil.tsx` | `/perfil`              |
| `index.tsx`   | Rota principal das tabs |


omo navegar entre telas

O Expo Router tem duas formas principais:

### 1) Navegação Declarativa (com <Link>)


````
import { Link } from "expo-router";

<Link href="/login">
  Ir para Login
</Link>

````

Essa forma é parecida com links de site.


### 2) Navegação Programática (com useRouter)

Ideal para botões:

````
import { useRouter } from "expo-router";

const router = useRouter();

router.push("/`filmes");

````
push = abre uma nova tela
back = volta



## 5. Como a navegação funciona na prática usando essa estrutura
 Para abrir a tela Home:


````
router.push("/(tabs)/screens/home");

````

Para ir para Serviços:

 ````

router.push("/(tabs)/screens/servicos");

````

Para voltar:

 ````

router.back();


````


## 6. Por que essa organização funciona tão bem?

Porque o Expo Router usa a estrutura de pastas como mapa da navegação:

Pasta indica grupo

Arquivo indica rota

_layout.tsx indica como o grupo funciona


## Resumindo:


“O Expo Router transforma pastas e arquivos em rotas.
A pasta (tabs) cria um grupo de navegação com abas.
O arquivo _layout.tsx define como essas abas funcionam.
A pasta screens contém as telas que aparecem dentro das tabs.
Navegar entre telas é tão simples quanto navegar entre arquivos.”

| Conceito          | Explicação                         |
| ----------------- | ---------------------------------- |
| **Arquivo**       | Se tornou uma tela                 |
| **Pasta**         | Se tornou uma rota ou um grupo     |
| **_layout.tsx**   | Controla a navegação daquele grupo |
| **Link**          | Vai para outra tela                |
| **router.push()** | Navegação via botão                |
| **router.back()** | Voltar                             |
| **params**        | Dados enviados pela URL            |



Abraços,

Prof. Dalvana Ribeiro
