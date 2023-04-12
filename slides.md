---
# try also 'default' to start simple
theme: default
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Apresentacao de conceitos basicos do angular
# persist drawings in exports and build
drawings:
  persist: false
colorSchema: 'dark'
# page transition
transition: slide-left
# use UnoCSS
css: unocss

fonts:
  mono: 'Fira Code'
---

# <carbon-logo-angular color="red" /> Workshop - Angular <carbon-logo-angular color="red" />


<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Pre-requisitos

- Node
- Npm
- Angular CLI - Versão 15.x - <tt>npm install -g @angular/cli</tt>
- .NET SDK 7.0 - [link](https://dotnet.microsoft.com/en-us/download/dotnet/7.0)
- (Recomendado) Docker & Docker Compose: [link](https://docs.docker.com/desktop/install/windows-install/)

- Baixar o repositório com a API: [Github](https://github.com/Yuri-Jordan/Asp-net-web-api-template)
- Baixar repositório com o frontend: [Github](https://github.com/edujtm/rent-cars-app)

---
layout: statement
---

# Estrutura do Workshop

---
layout: statement
---

<h1> 
Demo: construindo um componente no Angular
</h1>


<!--
Teste
-->

<!--
Here is another comment.
-->

---
layout: two-cols
---

# Exercício: Construir um componente de login

<div class="left-side">

1. Use ng generate para gerar um novo componente - <code>ng generate component pasta/nome-do-componente</code>

2. Adicione um input para o título do formulário

3. Adicione um output para o botão de submit

Documentação da biblioteca de componentes: [taiga-ui.dev](https://taiga-ui.dev/)
 - Input: [link](https://taiga-ui.dev/components/input#base)
 - InputPassword: [link](https://taiga-ui.dev/components/input-password#sizes)
 - Error: [link](https://taiga-ui.dev/components/error)

</div>

::right::

<div>

<span class="branch">Branch do exercício: exercise/1-components</span>
</div>

<div class="right-side">
Objetivo final

<img src="/imgs/exercise-1-final.png" />

<br/>

- Dica: O ng generate tem como pasta raiz a pasta <tt>./src/app</tt> (não é a pasta raiz do projeto).
</div>


<style>
.left-side {
  height: 80%;
  padding: 8px;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}

.right-side {
  height: 90%;
  padding: 30px;
  display: flex;
  flex-direction: column;
  justify-content: center; 
  align-items: center;
}

.right-side img {
  max-width: 300px;
}

.branch {
  color: lightgreen;
  font-weight: bold;
  font-size: 1.2em;
}
</style>

---
layout: statement
---

# Demo: Gerenciando Formulários no Angular

---
layout: two-cols
---

# Exercício: Criando FormGroup para o formulário de login


1. Crie um FormGroup para representar o campos do formulário de login

No formulário de registro de usuário:

1. Implemente um validador customizado para validar numero de telefone no formulário de registro

2. Implemente um validador customizado para validar que a senha deve ter:
   - pelo menos um digito
   - pelo menos um caracter maiúsculo
   - pelo menos um caracter minúsculo

::right::

<div>

<span class="branch">Branch do exercício: exercise/2-forms</span>
</div>

Para trocar de branch:

```bash
git add .
git stash
git checkout exercise/2-forms
```

Documentação:
  - FormGroup: [link](https://angular.io/guide/reactive-forms)
  - Custom Validators: [link](https://angular.io/guide/form-validation#defining-custom-validators)

<style>
.branch {
  color: lightgreen;
  font-weight: bold;
  font-size: 1.2em;
}


</style>



---
layout: statement
---

# Refatoração para módulos

---
layout: statement
---

# Demo: submetendo o formulário de registro

---
layout: two-cols
---

# Exercício: Submetendo o formulário de login

1. Utilize o HttpClient para submeter o formulário de login para a API

2. Salve as tokens de acesso no localStorage

3. Use o Router para redirecionar o usuário para a página de bookings

::right::

<div>

<span class="branch">Branch do exercício: exercise/3-httpclient</span>
</div>

Para trocar de branch:

```bash
git add .
git stash
git checkout exercise/3-httpclient
```

Documentação:
  - HttpClient - [link](https://angular.io/guide/http)
  - Router - [link](https://angular.io/api/router/Router#navigatebyurl)

<style>
.branch {
  color: lightgreen;
  font-weight: bold;
  font-size: 1.2em;
}
</style>

--- 
layout: statement
--- 

# Demo: criando service para tela de bookings

---
layout: two-cols
---

# Exercício: service para listagem de veículos

- Crie um service para listagem de veículos

- Registre o service no módulo específico

- Crie um BehaviorSubject para armazenar o resultado da requisição

- Associe o behaviorsubject ao template, associando-o à uma variável do componente ou usando o pipe async

::right::


<div>

<span class="branch">Branch do exercício: exercise/4-services</span>
</div>

Para trocar de branch:

```bash
git add .
git stash
git checkout exercise/4-services
```

Documentação:
  - AsyncPipe: [link](https://angular.io/guide/reactive-forms)

<style>
.branch {
  color: lightgreen;
  font-weight: bold;
  font-size: 1.2em;
}
</style>

---
layout: statement
---

# Demo: Criando HTTP interceptor

---
layout: two-cols
---

# Exercício: Crie um interceptor de token de autorização

<div class="right-side">
Crie um interceptor que obtem a token do local storage e adiciona
à requisição.

```ts
@Injectable()
export class UnauthorizedInterceptor implements HttpInterceptor {

  intercept(request: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
    return next.handle(request);
  }
}
```

Dica: 
a classe HttpRequest é imutável. Para modificá-la é necessário
usar o método `HttpRequest.clone()` passando um dicionário com
as propriedades que serão alteradas
</div>

::right::

<div>

<span class="branch">Branch do exercício: exercise/5-interceptors</span>
</div>

Para trocar de branch:

```bash
git add .
git stash
git checkout exercise/5-interceptors
```

Documentação:
  - Interceptors: [link](https://angular.io/guide/reactive-forms)
  - HttpRequest: [link](https://angular.io/api/common/http/HttpRequest#description)

<style>
.right-side {
  padding: 0px 10px;
}

.branch {
  color: lightgreen;
  font-weight: bold;
  font-size: 1.2em;
}
</style>