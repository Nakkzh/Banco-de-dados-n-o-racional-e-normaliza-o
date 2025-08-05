# Banco de dados, Não relacional e Normalização

### Banco de dados

Para entendermos os itens adiante primeiro precisamos ter noção e entedimento do que é um bancos de dados. Um banco de dados não é nada mais de uma coleção organizada de informações estruturadas, armazenadas eletronicamente em um sistema de computador, que permite a coleta, armazenamento, recuperação e manipulação de dados de maneira eficiente e estruturada.

`Imagine um grande arquivo onde você guarda informações sobre algo, como clientes, produtos, pedidos, etc. `

### Banco de dados *RELACIONAL*

Um banco de dados *RELACIONAL* é é um tipo de banco de dados que organiza dados em tabelas, com linhas e colunas, onde cada linha representa um registro e cada coluna representa um atributo.
<p align="center">
<img width="512" height="182" alt="image" src="https://github.com/user-attachments/assets/16124c7b-efb5-4a46-b402-ab5b07a73bb7" />
</p>

### Exemplos de uso:

- **Gestão de Estoque:** Um gerenciamento de estoque preciso e eficiente para garantir a satisfação do cliente e minimizar rupturas ou excesso de estoque. Os bancos de dados relacionais desempenham um papel crucial no gerenciamento e organização de grandes quantidades de dados de estoque para empresas
- **Registros Médicos Eletrônicos:** Organizações de saúde, como hospitais, clínicas e seguradoras, dependem de registros médicos eletrônicos (EMRs) precisos e seguros para fornecer atendimento eficiente ao paciente e agilizar as operações. Os bancos de dados relacionais são a base dos sistemas EMR, permitindo que os profissionais de saúde armazenem, gerenciem e analisem vastos dados de pacientes.
- **Mídias Sociais e Plataformas Online:** As mídias sociais e as plataformas online também aproveitam o poder dos bancos de dados relacionais para gerenciar dados do usuário e oferecer suporte a vários recursos, como gerenciamento de gráficos sociais, armazenamento de conteúdo e sistemas de recomendação.

---

### Banco de dados *NÃO* Relacional

Um banco de dados não relacional, também conhecido como NoSQL (Not Only SQL), é um tipo de sistema de gerenciamento de banco de dados que não utiliza o modelo tradicional de tabelas com linhas e colunas para armazenar dados, como os bancos de dados relacionais. Em vez disso, eles empregam modelos de dados mais flexíveis e adaptáveis, como chave-valor, documentos, colunas largas ou gráficos, para lidar com grandes volumes de dados não estruturados ou semiestruturados.

### Exemplos de uso:

- **Aplicativos de redes sociais:** Armazena perfis de usuário com diferentes estruturas (bio, interesses, links), Organiza posts, comentários e curtidas em formatos flexíveis, como documentos JSO.
- **Jogos online e multiplayer:** Armazena o progresso do jogador, inventários e estatísticas sem estrutura fixa. Lida com eventos simultâneos entre jogadores.,
- **Sistemas de recomendação de produtos:** Registra histórico de navegação e compras em tempo real. Analisa preferências e sugere produtos semelhantes.

---

### *Normalização* de dados

Normalização de banco de dados é um conjunto de regras que visa, principalmente, a organização de um projeto de banco de dados para reduzir a redundância de dados, aumentar a integridade de dados e o desempenho. Para normalizar o banco de dados, deve-se examinar as colunas (atributos) de uma entidade e as relações entre entidades (tabelas), com o objetivo de se evitar anomalias observadas na inclusão, exclusão e alteração de registros.

### Exemplos de uso:

- **Banco de Dados Relacional:**

-Objetivo:Evitar dados duplicados e melhorar integridade.

-Exemplo: Em vez de armazenar o nome do cliente repetidamente em uma tabela de pedidos, usa-se uma tabela separada de clientes com um ID único. A tabela de pedidos então referencia esse ID.

-Benefício: Redução de inconsistência e economia de espaço.

---

## Tabela não normalizada *EXEMPLO*

| Pedido(ID) | Nome do cliente | Endereço do cliente | ID do produto | Nome do produto | Quantidade | Preço total |
|------------|-----------------|---------------------|---------------|-----------------|------------|-------------|
| 1 | João Silva | Rua A, 123 | 10 | Caneta | 2 | 4,00 |
| 1 | João Silva | Rua A, 123 | 11 | Lápis | 1 | 2,00 |
| 2 | Maria Souza | Av, 456 | 10 | Caneta | 5 | 10,00 |

---

## Normalização até 3° forma *(3FN)*

### 1° forma

A Primeira Forma Normal (1FN) é o nível mais básico de normalização de bancos de dados relacionais. Ela estabelece as regras fundamentais para a organização dos dados em tabelas.

**Requisitos da 1FN:**
- **Eliminar repetições:** Cada tabela deve conter apenas valores atômicos (indivisíveis) em cada campo, sem grupos repetitivos ou arrays.
- **Valores atômicos:** Cada campo/coluna deve conter apenas um valor por registro (linha), não múltiplos valores combinados.
- **Identificador único:** Deve haver uma chave primária que identifique cada registro de forma única.

<p float="left">
<img width="409" height="188" alt="{6E3101DE-0D9B-49A9-9EBE-357383E4976B}" src="https://github.com/user-attachments/assets/58f33a35-537b-4ae0-bd58-85723b76bb8e" />
<img width="364" height="234" alt="{0CDC6963-F726-489F-9ED2-B146230518D8}" src="https://github.com/user-attachments/assets/430d5efb-79c8-426e-99a3-791baef0ed19" />
</p>

### 2° forma

A Segunda Forma Normal (2FN) é o próximo passo na normalização de bancos de dados após a Primeira Forma Normal. Ela lida especificamente com o problema das dependências parciais em tabelas que possuem chaves primárias compostas (com mais de um campo).

**Requisitos da 2FN:**
- **A tabela já deve estar na 1FN:** Todos os requisitos da Primeira Forma Normal devem ter sido atendidos.
- **Eliminar dependências parciais:** Todos os atributos não-chave devem depender totalmente da chave primária inteira (não apenas de parte dela).

<p float="left">
<img width="628" height="234" alt="{1752EDF6-F12D-4FC6-B64A-96933C2CE2F3}" src="https://github.com/user-attachments/assets/348eb048-aa8d-4f5b-a9c3-1be4303189d0" />
<img width="386" height="472" alt="{9BA54FAB-0ACD-4A17-983B-B6B78F319D22}" src="https://github.com/user-attachments/assets/e1a5af00-0701-4502-8998-c5b9c8e63679" />
</p>

### 3° forma

A Terceira Forma Normal (3FN) é o próximo nível de normalização após a 2FN, focando na eliminação de dependências transitivas entre os atributos de uma tabela.

**Requisitos da 3FN:**
- **A tabela já deve estar na 2FN:** Todos os requisitos da Segunda Forma Normal devem ter sido atendidos.
- **Eliminar dependências transitivas:** Nenhum atributo não-chave deve depender de outro atributo não-chave (devem depender apenas da chave primária).

<p float="left">
<img width="609" height="232" alt="{B9E3DC35-6F52-423C-B4F5-F1C5FD13E83E}" src="https://github.com/user-attachments/assets/d2c42bbe-b5a0-437c-98e2-8c43a472347c" />
<img width="371" height="478" alt="{1DEAE9FD-C54E-4DA6-944D-DED0BB4306E8}" src="https://github.com/user-attachments/assets/aa154b8e-0b40-4c11-8c99-ed3f0c5a7f51" />
</p>

---

## Estrutura não relacionada *(formato JSON)*

```JSON
{
  "pedido_id": 1,
  "cliente": {
    "nome": "Miguel",
    "endereco": "Rua bemalí, 71"
  },
  "itens": [
    {
      "produto_id": 54,
      "nome": "garrafa termica",
      "quantidade": 2,
      "preco_total": 66.00
    },
    {
      "produto_id": 111,
      "nome": "Churrasqueira",
      "quantidade": 1,
      "preco_total": 300.00
    }
  ]
}
```

Em bancos de dados relacionais, a normalização evita redundâncias e organiza os dados em múltiplas tabelas. Porém, isso requer diversas operações para reunir os dados, o que pode impactar o desempenho em consultas simples ou frequentes.

Já em modelos não relacionais, como o formato **JSON:**
- Dados relacionados estão agrupados: Informações do cliente e itens estão juntos no mesmo documento, sem a necessidade de tabelas separadas.
- Consulta direta e mais rápida: Ideal para aplicações que acessam o pedido completo com frequência.
- Flexibilidade de estrutura: Permite armazenar campos variáveis sem alterar o esquema geral.
