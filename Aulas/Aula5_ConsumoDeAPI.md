#   **Aula 5: Consumo de API no React Native (Expo)**  
## **Como buscar dados, organizar serviços e consumir APIs **

---

##  Links Importantes  
- **API Studio Ghibli:** https://ghibliapi.vercel.app/films  
- **MDN Fetch API:** https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API  
- **React Native Networking:** https://reactnative.dev/docs/network  
- **Projeto Base (Filmes Studio Ghibli):**   https://github.com/DalvanaRibeiro/AppFilmes241N

---

## 1. O que é uma API?

Uma **API** é um serviço na internet que fornece dados para o seu aplicativo.  
Ela funciona como um restaurante:

- Você faz um **pedido** → *request*  
- O garçom entrega a **resposta** → *response*  

No nosso caso:

**O app React Native** → pede filmes  
**API Studio Ghibli** → devolve lista de filmes

---

## 2. Por que consumir APIs no React Native?

- Exibir dados reais  
- Buscar filmes, produtos, usuários, clima  
- Apps mais dinâmicos e atualizados  
- Muito usado em projetos profissionais  

---

## 3. A API usada: Filmes do Studio Ghibli

https://ghibliapi.vercel.app/films

Ela retorna algo assim: 


````

Ela retorna algo assim:

```json
{
  "id": "123",
  "title": "Meu Amigo Totoro",
  "image": "https://...",
  "release_date": "1988"
}

````
## 4. Organização do projeto:

<img width="273" height="805" alt="image" src="https://github.com/user-attachments/assets/ccc8cca4-e85c-4caa-bff8-635f3abcf94c" />

O arquivo api.ts :

Vamos entender passo a passo o código que busca os filmes do Studio Ghibli.

---

### 🎬 4.1. Tipo dos Dados (TypeScript)

```ts
export type Filme = {
  id: string
  title: string
  image: string
  release_date: string
}
````

O que isso significa?

Estamos dizendo como é o formato de um filme.

Um filme DEVE ter:

id → identificação única

title → nome

image → foto do poster

release_date → ano de lançamento

Isso ajuda o TypeScript a avisar caso você tente acessar coisas que não existem.

É como dizer:

“Um filme sempre terá estas 4 características.”

### 4.2. Função que busca TODOS os filmes:

````
export async function buscarFilmesPopulares(): Promise<Filme[]> {

````
Por que async e Promise?

async permite usar await dentro da função.

Promise<Filme[]> significa:

“Esta função promete devolver uma lista de filmes.”

### 4.3. Fazendo o pedido para a API

````
const resp = await fetch("https://ghibliapi.vercel.app/films")

````

fetch() é o garçom digital.

Ele vai até a API e traz os dados.

await significa: “espere o garçom voltar.”

4.4. Convertendo resposta em JSON

````
const dados = await resp.json()

````


A API envia os dados como texto.
Aqui transformamos em objeto JavaScript, fácil de usar.


4.5 Garantindo que a resposta é uma lista

````
if (!Array.isArray(dados)) return []

````

Isso garante que, se a API falhar, seu app não vai quebrar.

 Evita erro tipo: “map não é função”.

 4.6 Preparando os objetos do jeito que queremos
 
````
return dados.map((f: any) => ({
  id: f.id,
  title: f.title,
  image: f.image,
  release_date: f.release_date
}))

````
 Por que map?

A API entrega MUITA informação.

Mas você só precisa de 4 campos.

O map() cria um novo conjunto só com o que interessa.

É como “limpar” os dados e deixar só o essencial.

4.7 Tratando erros


````
} catch (erro) {
  console.error("Erro em buscarFilmesPopulares:", erro)
  return []
}


````
Se algo der errado:

Sem internet

API fora do ar

URL errada

→ O app não trava
→ Apenas devolve uma lista vazia

 4.8 Buscar filmes por nome

````
export async function buscarFilmesPorNome(nome: string): Promise<Filme[]> {

````
O que isso faz?

Busca todos os filmes

Filtra apenas os que combinam com o texto digitado

````
return todos.filter(f =>
  f.title.toLowerCase().includes(nome.toLowerCase())
)

````

 includes() → funciona como “contains”
 
  Pesquisa ignorando maiúsculas e minúsculas

Perfeito para search bar.

4.9 Consumindo a API dentro da tela filmes.tsx

Agora vamos ver como esses dados chegam na tela.

 4.10 Criamos um estado para guardar a lista

 
````
const [filmes, setFilmes] = useState<Filme[]>([])

````

filmes → guarda os filmes

setFilmes → atualiza os filmes

O tipo é lista de Filme

 4.11 Buscar ao ABRIR a tela (useEffect)


````
useEffect(() => {
  async function carregar() {
    const resposta = await buscarFilmesPopulares()
    setFilmes(resposta)
  }
  carregar()
}, [])

````

 Resumindo:

useEffect() funciona como:

“Assim que essa tela aparecer, execute este código.”

Ele chama a função da API

Guarda os filmes no estado

Atualiza automaticamente a tela

### 5. Exibindo os filmes com FlatList

 
````
<FlatList
  data={filmes}
  keyExtractor={item => item.id}
  renderItem={({ item }) => (
    <View style={styles.card}>
      <Image source={{ uri: item.image }} style={styles.poster} />
      <Text style={styles.nome}>{item.title}</Text>
      <Text style={styles.ano}>Ano: {item.release_date}</Text>
    </View>
  )}
/>

````
Por que FlatList?

Não trava o app

Carrega itens sob demanda

Ideal para listas grandes

Melhor performance

 5. Como funciona o ciclo completo
1. A tela abre

useEffect() roda automaticamente.

2. A função da API é chamada

buscarFilmesPopulares()

3. O fetch busca os dados na internet

O app espera (await).

 4. A resposta é convertida em JSON

resp.json()

 5. Os dados são filtrados e limpos

map()

 6. O estado recebe os filmes

setFilmes(resposta)

 7. A tela é renderizada novamente

FlatList mostra os filmes

### Resumindo:

| Conceito            | Explicação                      |
| ------------------- | ------------------------------- |
| **API**             | Lugar que fornece dados         |
| **fetch()**         | Requisição para a API           |
| **json()**          | Converte resposta para objeto   |
| **async/await**     | Espera a resposta chegar        |
| **try/catch**       | Evita erros que travariam o app |
| **map()**           | Limpa e organiza os dados       |
| **filter()**        | Busca por nome                  |
| **useEffect()**     | Executa ao abrir a tela         |
| **useState()**      | Guarda os filmes                |
| **FlatList**        | Lista rápida e performática     |
| **services/api.ts** | Organização profissional        |


Abraços,

Prof. Dalvana Ribeiro
