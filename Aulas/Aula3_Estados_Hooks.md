#   **Aula 3: Estados e Hooks no React Native**  
## **useState, useEffect, Hooks Essenciais e Funcionamento Didático**

---

##  Links Importantes
- **Documentação Oficial dos Hooks:** https://react.dev/reference/react
- **Link da Aula 3:**   https://www.canva.com/design/DAGvTyohC9s/qPjXc6TqlWx2kUJI1v-7SQ/edit?utm_content=DAGvTyohC9s&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
- **Projeto Base de Hooks:** *https://github.com/DalvanaRibeiro/HooksReactNative*
- **Projeto: Classificador de Animes:** *https://github.com/DalvanaRibeiro/classificaAnime*



---

#  1. O que são Estados no React Native?

Um **estado** (state) é uma informação que **muda ao longo do tempo** dentro do componente.

- Se o estado muda → a tela **re-renderiza** automaticamente  
- O estado é a “memória” viva do componente


![Exemplo useState](https://raw.githubusercontent.com/DalvanaRibeiro/UC15_241N_ComponentesPrincipais/main/my-app/assets/images/usestate2.gif)

Usamos estado para:
- nome digitado  
- contador  
- tema claro/escuro  
- dados vindos da API  
- formulários  
- listas dinâmicas  

---

## O Hook `useState`

O `useState` permite criar e atualizar estados em componentes funcionais.

### Sintaxe:
````jsx
const [valor, setValor] = useState(valorInicial);
````
valor → estado atual

setValor → função que altera o estado

Exemplo:

````
export default function App() {
  const [nome, setNome] = useState("");

  return (
    <View style={{ padding: 20 }}>
      <TextInput 
        placeholder="Digite seu nome"
        onChangeText={texto => setNome(texto)}
        style={{ borderWidth: 1, padding: 10 }}
      />

      <Text style={{ marginTop: 20, fontSize: 20 }}>
        Olá, {nome}!
      </Text>
    </View>
  );
}

````
## O Hook useEffect (Ciclo de Vida)

O useEffect controla as etapas do ciclo de vida:

Montagem → quando o componente aparece

Atualização → quando o estado muda

Desmontagem → quando o componente desaparece

- Montagem (Mount)

````
useEffect(() => {
  console.log("Montou!");
}, []);

````

- Atualização (Update)

````
useEffect(() => {
  console.log("Atualizou!");
}, [contador]);


````


- Desmontagem (Unmount)

````
useEffect(() => {
  return () => console.log("Desmontou!");
}, []);


````

## Outros Hooks Importantes
## useRef

Guarda valores que não causam re-render.

````
const inputRef = useRef(null);

````



## useMemo

Memoriza cálculos pesados.


````
const resultado = useMemo(() => calcular(x), [x]);

````

## useContext

O useState funciona apenas dentro do componente, mas e quando precisamos compartilhar valores entre várias telas?

Exemplos:

- Nome do usuário

- Tema (claro/escuro)

- Login

- Carrinho de compras



Para isso existe o useContext, que cria um estado global — acessível de qualquer componente.

Como funciona o useContext?

Ele usa dois passos:

1. Criar um Contexto

2. Envolver a aplicação no Provider

3. Consumir o contexto em qualquer tela usando useContext


1. Criando um Contexto

Crie uma pasta:

````
/context/userContext.tsx

````

e dentro: 

````
import { createContext, useContext, useState } from "react";

const UserContext = createContext();

export function UserProvider({ children }) {
  const [nome, setNome] = useState("");

  return (
    <UserContext.Provider value={{ nome, setNome }}>
      {children}
    </UserContext.Provider>
  );
}

export function useUser() {
  return useContext(UserContext);
}

````

- createContext()

Cria o “espaço” onde vamos guardar os dados globais.

- UserProvider

É o pai global.
Ele entrega os valores para todas as telas usando:

````
<UserContext.Provider value={{ nome, setNome }}>

````

2. Envolver a aplicação com o Provider

No Expo Router, isso fica no arquivo:

_layout.tsx, OU

app/index.tsx, OU

App.js

Exemplo: 


````
import { UserProvider } from "../context/userContext";
import { Slot } from "expo-router";

export default function Layout() {
  return (
    <UserProvider>
      <Slot />
    </UserProvider>
  );
}

````

3. Usando o Contexto em qualquer tela

````
import { useUser } from "../context/userContext";

export default function Home() {
  const { nome, setNome } = useUser();

  return (
    <View style={{ padding: 20 }}>
      <Text>Nome atual: {nome}</Text>

      <TouchableOpacity
        onPress={() => setNome("Professora Dalvana")}
        style={{
          marginTop: 20,
          backgroundColor: "#00856F",
          padding: 10,
          borderRadius: 8
        }}
      >
        <Text style={{ color: "white", textAlign: "center" }}>Trocar Nome</Text>
      </TouchableOpacity>
    </View>
  );
}

````



| **Conceito**                  | **Explicação fácil**                                   |
|------------------------------|---------------------------------------------------------|
| **Context**                  | A *mochila* onde guardamos dados globais               |
| **Provider**                 | Quem entrega a mochila para todas as telas             |
| **useContext**               | O hook que pega algo de dentro da mochila              |
| **useState dentro do Provider** | Onde guardamos valores globais (nome, tema, login…) |


## useCallback

Memoriza funções.

````
const handleClick = useCallback(() => {
  console.log("clicou!");
}, []);

````

Abraços,

Prof. Dalvana Ribeiro
