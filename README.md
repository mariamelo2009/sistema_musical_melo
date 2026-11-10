# sistema_musical_melo
# 🎵 Sistema Musical

## 📌 Sobre o Projeto

O **Sistema Musical** é uma aplicação web desenvolvida em **PHP** integrada ao banco de dados **MySQL**, criada com o objetivo de permitir o gerenciamento de artistas e músicas.

O sistema possui uma área de acesso para usuários e, após o login, apresenta um menu principal com opções para gerenciar artistas, cadastrar músicas e acessar a biblioteca musical.

A aplicação utiliza banco de dados relacional para armazenar as informações dos usuários, artistas e músicas.

---

## 🎯 Objetivo da Atividade

O objetivo da atividade é desenvolver um sistema CRUD utilizando **PHP e MySQL**, aplicando conceitos de:

- Conexão entre PHP e MySQL;
- Criação e utilização de banco de dados;
- Cadastro de informações;
- Consulta de dados;
- Edição de registros;
- Exclusão de registros;
- Relacionamento entre tabelas;
- Upload e armazenamento de imagens;
- Validação de informações;
- Utilização de sessões para controle de acesso;
- Integração com links do YouTube.

---

## 🛠️ Tecnologias Utilizadas

- **PHP**
- **MySQL**
- **HTML5**
- **CSS3**
- **MySQLi**
- **Git e GitHub**

---

## 🗄️ Banco de Dados

O banco de dados utilizado no projeto se chama:

```sql
sistema_musical_v2
```

O banco possui três tabelas principais:

### 👤 Tabela `usuarios`

Armazena os usuários que podem acessar o sistema.

| Campo | Tipo | Descrição |
|---|---|---|
| `id` | INT | Identificador único |
| `usuario` | VARCHAR(50) | Nome do usuário |
| `senha` | VARCHAR(255) | Senha criptografada |

A tabela possui um usuário padrão cadastrado no banco.

---

### 🎤 Tabela `artistas`

Armazena os dados dos artistas cadastrados no sistema.

| Campo | Tipo | Descrição |
|---|---|---|
| `id` | INT | Identificador único |
| `nome` | VARCHAR(100) | Nome do artista |
| `genero` | VARCHAR(50) | Gênero musical |
| `pais` | VARCHAR(50) | País de origem |
| `imagem` | VARCHAR(255) | Caminho da imagem |



---

### 🎵 Tabela `musicas`

Armazena as músicas relacionadas aos artistas.

| Campo | Tipo | Descrição |
|---|---|---|
| `id` | INT | Identificador único |
| `artista_id` | INT | ID do artista |
| `titulo` | VARCHAR(100) | Título da música |
| `album` | VARCHAR(100) | Álbum |
| `genero` | VARCHAR(50) | Gênero musical |
| `youtube_link` | VARCHAR(255) | Link do vídeo no YouTube |
| `letra` | TEXT | Letra da música |
| `imagem_capa` | VARCHAR(255) | Caminho da capa |

A coluna `artista_id` é uma chave estrangeira relacionada à tabela `artistas`. Dessa forma, cada música pode ser associada a um artista cadastrado.

---

## 📂 Estrutura dos Arquivos

```text
📁 Sistema Musical
│
├── 📄 index.php
├── 📄 conexao.php
├── 📄 cadastro_artista.php
├── 📄 cadastro_musica.php
├── 📄 geraSenha.php
├── 📄 bd.sql
│
├── 📄 login.php
├── 📄 logout.php
├── 📄 valida_sessao.php
├── 📄 listagem_musicas.php
│
├── 📁 img/
│   └── imagens dos artistas e capas
│
└── 📄 styles.css
```

> Os arquivos `login.php`, `logout.php`, `valida_sessao.php`, `listagem_musicas.php` e `styles.css` fazem parte da estrutura utilizada pelo sistema, embora não estejam entre os arquivos principais enviados nesta atividade.

---

## 🔌 Conexão com o Banco de Dados

O arquivo `conexao.php` é responsável por realizar a conexão entre a aplicação PHP e o MySQL.

A conexão utiliza:

```php
$servername = "localhost";
$username   = "root";
$password   = "Senai@118";
$dbname     = "sistema_musical_v2";
```

A conexão é realizada através da classe `mysqli` e o sistema utiliza `utf8mb4` para permitir caracteres especiais, acentos e emojis.

O arquivo também verifica se a pasta `img` existe e, caso não exista, cria o diretório automaticamente para armazenar as imagens.

---

## 🎤 Cadastro de Artistas

O arquivo:

```text
cadastro_artista.php
```

é responsável pelo gerenciamento dos artistas.

O sistema permite:

- Cadastrar novos artistas;
- Editar artistas existentes;
- Excluir artistas;
- Visualizar artistas cadastrados;
- Adicionar foto do artista;
- Redimensionar imagens;
- Validar o tipo e tamanho da imagem;
- Acessar as músicas relacionadas ao artista.

O cadastro utiliza operações **CRUD**:

```text
C → Create
R → Read
U → Update
D → Delete
```

Essas operações estão implementadas no próprio arquivo de cadastro de artistas.

### 🖼️ Upload de imagens

As imagens dos artistas podem ser enviadas nos formatos:

```text
JPG
JPEG
PNG
```

O tamanho máximo permitido é de **5 MB**.

O sistema também redimensiona as imagens para aproximadamente **300 × 300 pixels** antes de salvá-las.

---

## 🎵 Cadastro de Músicas

O arquivo:

```text
cadastro_musica.php
```

é responsável pelo cadastro e gerenciamento das músicas.

É possível cadastrar:

- Artista;
- Título;
- Álbum;
- Gênero;
- Link do YouTube;
- Letra da música;
- Capa do álbum.

Cada música possui uma relação com um artista através do campo:

```text
artista_id
```

que funciona como chave estrangeira.

---

## ▶️ Integração com YouTube

O sistema permite cadastrar o link de um vídeo do YouTube.

A aplicação identifica o ID do vídeo a partir de diferentes formatos de URL, como:

```text
https://www.youtube.com/watch?v=...
https://www.youtube.com/embed/...
https://www.youtube.com/v/...
https://youtu.be/...
```

Depois, o sistema utiliza esse ID para gerar o link de acesso ao vídeo.

---

## 🖼️ Capa das Músicas

Assim como acontece com os artistas, o sistema permite enviar uma imagem para representar a capa do álbum.

São aceitos:

```text
JPG
JPEG
PNG
```

com limite de **5 MB**.

A imagem também é redimensionada antes de ser armazenada.

---

## ✏️ Edição e Exclusão

O sistema permite editar os dados cadastrados.

Na edição de um artista ou música, caso uma nova imagem não seja enviada, a imagem existente pode ser mantida.

Também é possível excluir registros.

No caso dos artistas, existe uma verificação para impedir a exclusão quando o artista possui músicas cadastradas.

Já na exclusão de músicas, o sistema também remove o arquivo físico correspondente à capa antes de excluir o registro do banco.

---

## 🏠 Menu Principal

O arquivo `index.php` funciona como o menu principal do sistema.

Após o login, o usuário pode acessar:

### 🎤 Gerenciar Artistas

Permite cadastrar e editar artistas.

### 🎵 Cadastrar Músicas

Permite adicionar músicas ao sistema.

### 🎼 Biblioteca Musical

Permite visualizar e filtrar as músicas cadastradas.

O acesso ao menu é protegido pela validação de sessão.

---

## 🔐 Sistema de Login

O projeto utiliza controle de sessão para restringir o acesso às páginas do sistema.

O arquivo `index.php`, por exemplo, inclui:

```php
include('valida_sessao.php');
```

Dessa forma, somente usuários autenticados conseguem acessar o menu principal.

---

## 🔑 Geração de Senha

O arquivo `geraSenha.php` é utilizado para gerar uma senha criptografada utilizando `password_hash()` com o algoritmo `PASSWORD_BCRYPT`.

Exemplo utilizado no projeto:

```php
echo password_hash('123', PASSWORD_BCRYPT);
```



---

## ⚙️ Como Executar o Projeto

### 1. Instalar um servidor local

É necessário possuir um ambiente capaz de executar PHP e MySQL, como:

- XAMPP;
- WAMP;
- Laragon.

---

### 2. Colocar o projeto no servidor

Coloque a pasta do projeto dentro da pasta correspondente ao servidor local.

No XAMPP, por exemplo:

```text
C:\xampp\htdocs\
```

---

### 3. Criar o banco de dados

Abra o **phpMyAdmin** ou outro programa de gerenciamento do MySQL.

Execute o arquivo:

```text
bd.sql
```

Esse arquivo cria o banco:

```sql
sistema_musical_v2
```

e também cria as tabelas necessárias para o funcionamento do sistema.

---

### 4. Configurar a conexão

Verifique o arquivo:

```text
conexao.php
```

e confirme se os dados de acesso ao MySQL correspondem ao seu ambiente.

Exemplo:

```php
$servername = "localhost";
$username   = "root";
$password   = "Senai@118";
$dbname     = "sistema_musical_v2";
```

---

### 5. Iniciar o servidor

Inicie:

```text
Apache
MySQL
```

no XAMPP ou no servidor local utilizado.

---

### 6. Acessar o sistema

No navegador, acesse o endereço correspondente à pasta do projeto, por exemplo:

```text
http://localhost/nome-da-pasta/
```

---

## 🧪 Funcionalidades Principais

| Funcionalidade | Status |
|---|---|
| Login de usuário | ✅ |
| Controle de sessão | ✅ |
| Cadastro de artistas | ✅ |
| Edição de artistas | ✅ |
| Exclusão de artistas | ✅ |
| Upload de foto | ✅ |
| Cadastro de músicas | ✅ |
| Edição de músicas | ✅ |
| Exclusão de músicas | ✅ |
| Upload de capa | ✅ |
| Link do YouTube | ✅ |
| Cadastro de letra | ✅ |
| Relacionamento artista/música | ✅ |
| Biblioteca musical | ✅ |

---

## 📚 Conceitos Trabalhados

Durante o desenvolvimento da atividade foram utilizados conceitos importantes de desenvolvimento web, como:

- Programação em PHP;
- HTML;
- CSS;
- Banco de dados MySQL;
- SQL;
- CRUD;
- Chaves primárias;
- Chaves estrangeiras;
- Relacionamento entre tabelas;
- Sessões;
- Upload de arquivos;
- Validação de dados;
- Manipulação de imagens;
- Hash de senhas;
- Consultas preparadas com `mysqli`.

---

## 👩‍💻 Desenvolvedora

**Maria Eduarda de Souza Melo**

Projeto desenvolvido como atividade acadêmica para prática de desenvolvimento web utilizando **PHP e MySQL**.

---

## 📄 Licença

Este projeto foi desenvolvido para fins **educacionais e acadêmicos**.
