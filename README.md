<div> 
<p><a href="https://github.com/JosiTubaroski/Controllers_Services/blob/main/README.md">Home</a></p>
</div> 


# Agora vamos criar a nossa Controllers

<img src="https://github.com/JosiTubaroski/Controllers_Services/blob/main/img/20250226_Criando_Controller.png"/>

### O Controler será do tipo API

<img src="https://github.com/JosiTubaroski/Controllers_Services/blob/main/img/Controlers/02_Controler_API.png"/>

### Criando a AutorController.cs

<img src="https://github.com/JosiTubaroski/Controllers_Services/blob/main/img/Controlers/03_Criando_Autor_Controler.png"/>

Veja o código da AutorController.cs 👉 https://github.com/JosiTubaroski/Controllers_Services/blob/main/img/Controlers/AutorController.cs

### Código Explicado.

Esse código define um <b>controller</b> para uma API no <b>ASP.NET Core,</b> resposável por gerenciar autores.
Vamos detalhar cada parte:

### 🔹 Namespaces Importados

Essas linhas trazem funcionalidades necessárias para o código:

<img src="https://github.com/JosiTubaroski/AutorController/blob/main/img/03_Bibliotecas.png"/>

### 🔹 Definição do Controller

<img src="https://github.com/JosiTubaroski/AutorController/blob/main/img/04_Definindo_API_Controller.png"/>

- <b>[Route("api/[controller]")]</b> → Define que este controller responderá às requisições no endpoint api/Autor
- <b>[ApiController] </b> → Indica que essa classe é um controller de API no ASP.NET Core.
- <b> AutorController : ControllerBase </b>  → Estende a classe ControllerBase, que fornece funcionalidades básicas para um controller.

### 🔹 Injeção de Dependência

<img src="https://github.com/JosiTubaroski/AutorController/blob/main/img/06_Injecao_Dependencia.png"/>

- O AutorController recebe no construtor uma instância da interface IAutorInterface, que representa um serviço de autores.
- _autorInterface armazena essa instância para ser usada dentro do controller.
- Esse padrão segue a <b>Injeção de Dependência</b>, permitindo maior flexibilidade e testabilidade do código.

### 🔹 Definição do Método GET

<img src="https://github.com/JosiTubaroski/AutorController/blob/main/img/07_Listar_Autores.png"/>

- 🔹 Explicação:

  1. [HttpGet("ListarAutores")] → Indica que esse método será acessado via requisição HTTP GET no endpoint api/Autor/ListarAutores.
  2. Task<ActionResult<ResponseModel<List<AutorModel>>>> →
     - Task<> → O método é assíncrono (usa await).
     - ActionResult<> → Retorna um resultado HTTP com status adequado.
     - ResponseModel<List<AutorModel>> → Retorna uma resposta estruturada contendo uma <b>lista de autores.</b>

 3. await _autorInterface.ListarAutores(); → Chama o serviço que busca a lista de autores no banco de dados.
 4. return Ok(autores); → Retorna um status 200 OK com os autores.

### 🔹 Fluxo Resumido

- 1️⃣ O usuário faz uma requisição GET para api/Autor/ListarAutores.
- 2️⃣ O método ListarAutores() chama _autorInterface.ListarAutores(), que provavelmente busca os dados no banco.
- 3️⃣ Os dados são retornados dentro de um objeto ResponseModel.
- 4️⃣ A API responde com 200 OK e a lista de autores.

### 🔹 Resumo Geral

- ✅ Define um controller no ASP.NET Core para gerenciar autores.
- ✅ Utiliza Injeção de Dependência para chamar serviços sem acoplamento direto.
- ✅ Implementa um endpoint GET para listar autores.
- ✅ Usa programação assíncrona (async/await) para melhor desempenho.






