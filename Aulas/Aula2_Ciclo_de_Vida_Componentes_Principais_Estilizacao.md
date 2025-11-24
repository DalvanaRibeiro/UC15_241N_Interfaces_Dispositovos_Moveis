#   **Aula 2: Ciclo de Vida, Componentes Principais e Estilização**  
## **Componentes, Estilização, Sintaxe, Ciclo de Vida e TSX**


---

##  Links Importantes
- **Link da Aula 2:** https://www.canva.com/design/DAGojCv1lmA/G5JgXoBpsi_ZpL2GA-tiZg/edit?utm_content=DAGojCv1lmA&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
- **Documentação Oficial:** https://reactnative.dev/  
- **Projeto da Aula:** https://github.com/DalvanaRibeiro/UC15_241N_ComponentesPrincipais  

---

##  1. Sintaxe do React Native (JSX)

React Native usa **JSX**, uma sintaxe que mistura **JavaScript + XML**  
Isso permite escrever estrutura visual dentro do código:

```jsx
<View>
  <Text>Olá!</Text>
</View>
````
Por que a sintaxe é assim?

- O JSX deixa o código mais intuitivo

- Permite compor interfaces como blocos

- Facilita quando a UI depende de lógica

- O React converte JSX para chamadas nativas internas

# Ciclo de Vida no React Native

O React Native segue o ciclo de vida do React, baseado em componentes funcionais + Hooks.

 Por que isso importa?

Porque sua tela sofre mudanças ao longo do tempo:

- quando é criada,

- quando é atualizada,

- quando é destruída.

E você precisa rodar lógicas nesses momentos.

##
### O Ciclo de Vida Moderno (com Hooks)

Um componente pode ser entendido como um pequeno bloco de código responsável por exibir algo na tela. Ele aparece para o usuário, pode mudar quando ocorre alguma interação (como um clique ou digitação) e, em certos momentos, pode até deixar de existir na interface.

Por isso, cada componente passa por um ciclo de vida, que representa todas as etapas desde o momento em que ele é criado até o momento em que é removido da tela. Esse ciclo começa na fase de montagem, quando o componente é exibido pela primeira vez, passa pela fase de atualização, quando ele reage a mudanças de dados, e termina na fase de desmontagem, quando deixa de ser renderizado.

A Figura abaixo ilustra essas etapas de forma visual, mostrando como o componente nasce, se atualiza e, eventualmente, é destruído.




<div style="position: relative; min-height: 500px;">
  <img src="https://github.com/DalvanaRibeiro/UC15_241N_ComponentesPrincipais/blob/main/my-app/assets/images/ciclovida.png" alt="Imagem do Curso" width: 500px;"/>
</div>


O React Native atual usa Funções + useEffect.

O useEffect controla o ciclo de vida:

````
useEffect(() => {
  console.log("Componente montou!");

  return () => {
    console.log("Componente desmontou!");
  };
}, []);


``````
- Montagem (Mount)

Quando a tela aparece pela primeira vez.

Buscar dados na API

Carregar informações do usuário

````
useEffect(() => {...}, [])
````
- Atualização (Update)

Quando um estado ou prop muda:


````
const [contador, setContador] = useState(0);

useEffect(() => {
  console.log("Contador mudou:", contador);
}, [contador]);

````

- Desmontagem (Unmount)

Quando o usuário sai da tela.

Limpar eventos

Encerrar timers

Fechar conexões


````
useEffect(() => {
  return () => console.log("Saiu da tela");
}, []);

````
---

## Por que estamos trabalhando com TSX nas aplicações?

TSX = TypeScript + JSX

É a combinação da sintaxe JSX com o poder do TypeScript.

 1. TypeScript evita erros antes de rodar

- Verifica tipos

- Impede chamadas inválidas

- Mostra erros no editor

2. Autocompletar poderoso

TSX entende:

- propriedades dos componentes

- tipos nativos do RN

- bibliotecas externas

3. Código mais organizado

Você sabe exatamente:

- o tipo de um parâmetro

- o que cada propriedade aceita

- o que uma função retorna

4. Facilita projetos grandes

React Native é usado em apps enormes.
TypeScript deixa o projeto:

- mais estável

- mais fácil de manter

- menos bugado

---
##  Componentes Principais do React Native

React Native **não usa HTML**, mas sim **componentes nativos equivalentes** que são traduzidos diretamente para elementos reais do Android e iOS.


 1. **View**
A **View** é o bloco fundamental da interface no React Native.

- Funciona como a `<div>` do HTML  
- Serve para agrupar elementos  
- Ajuda na organização do layout  
- Sempre recebe estilos (altura, largura, cores, alinhamento)

 Exemplo:
```jsx
<View style={{ padding: 20, backgroundColor: '#e0f7ec' }}>
  <Text>Dentro de uma View!</Text>
</View>
````

2. Text

Componente exclusivo para mostrar textos.

Diferente do HTML, você não pode colocar texto solto dentro de uma View.
Todo texto deve estar dentro de um <Text>.

Exemplo:

````
<Text style={{ fontSize: 22, fontWeight: 'bold' }}>
  Olá, React Native!
</Text>

````


3. Image

Exibe imagens locais ou remotas (da internet).

Exemplo:

````
<Image 
  source={{ uri: "https://reactnative.dev/img/tiny_logo.png" }} 
  style={{ width: 100, height: 100 }} 
/>

````

4. ScrollView

Cria uma área com rolagem, permitindo que conteúdos grandes caibam na tela.

Ideal para:

textos grandes

formulários longos

múltiplos componentes

Exemplo:

````
<ScrollView style={{ padding: 20 }}>
  <Text>Muito conteúdo rolável aqui...</Text>
</ScrollView>

````

5. TextInput

Campo usado para entrada de texto pelo usuário.

Tem placeholder

Pode receber teclado numérico

Pode ser controlado com estado

Alta personalização

Exemplo:



````

<TextInput
  placeholder="Digite seu nome"
  style={{
    borderWidth: 1,
    padding: 10,
    borderRadius: 8,
    marginTop: 10
  }}
/>

````


6. TouchableOpacity / Pressable

Componentes usados como botões.

- TouchableOpacity

O botão fica “mais transparente” quando pressionado

Muito usado, simples e direto

Exemplo:

````
<TouchableOpacity 
  style={{
    backgroundColor: '#00856F',
    padding: 12,
    borderRadius: 8,
    marginTop: 10
  }}
>
  <Text style={{ color: '#fff', textAlign: 'center' }}>Enviar</Text>
</TouchableOpacity>

````

7. FlatList

Componente ideal para listas grandes e dinâmicas.

Muito performático

Renderiza apenas os itens visíveis

Possui item separator, header, footer e muito mais

Exemplo:

````
<FlatList
  data={[{ id: '1', nome: 'Item 1' }, { id: '2', nome: 'Item 2' }]}
  renderItem={({ item }) => <Text>{item.nome}</Text>}
  keyExtractor={item => item.id}
/>

````


A tabela abaixo resume os principais componentes usados no dia a dia:

| **Componente**              | **Função**                          |
|-----------------------------|--------------------------------------|
| **View**                    | Div nativa, estrutura/layout         |
| **Text**                    | Exibir textos                        |
| **Image**                   | Mostrar imagens                      |
| **ScrollView**              | Conteúdo rolável                     |
| **TextInput**               | Campo de digitação do usuário        |
| **TouchableOpacity** / **Pressable** | Botões e ações              |
| **FlatList**                | Listas grandes e performáticas       |

----

## Estilização no React Native

React Native não usa CSS tradicional.
Os estilos são feitos com objetos JavaScript usando camelCase:

Características:

Sem classes CSS

Sem arquivos .css

Estilo inline ou com StyleSheet.create()

Tudo baseado em Flexbox

Propriedades em camelCase

Exemplo: 

````
const styles = StyleSheet.create({
  titulo: {
    fontSize: 22,
    color: "#00856F",
    fontWeight: "bold"
  },
});

````

uso: 

````
<Text style={styles.titulo}>Olá!</Text>

````

Abraços

Prof. Dalvana Ribeiro
