# ✨ Lumina — Loja de Moda & Variedades

> Loja virtual moderna com autenticação via Supabase, carrinho de compras e finalização de pedidos pelo WhatsApp.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)

---

## 📋 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades](#-funcionalidades)
- [Tecnologias](#-tecnologias)
- [Pré-requisitos](#-pré-requisitos)
- [Como Usar](#-como-usar)
- [Configuração do Supabase](#-configuração-do-supabase)
- [Personalização](#-personalização)
- [Estrutura do Projeto](#-estrutura-do-projeto)
- [Screenshots](#-screenshots)
- [Contribuição](#-contribuição)
- [Licença](#-licença)

---

## 📖 Sobre o Projeto

**Lumina** é uma loja virtual de página única (SPA) desenvolvida com HTML, CSS e JavaScript puro. O projeto foi pensado para pequenos empreendedores do setor de moda que desejam ter uma vitrine online elegante, com sistema de login real e fluxo de vendas integrado ao WhatsApp — sem precisar de back-end próprio.

A autenticação e o gerenciamento de usuários são feitos inteiramente via **Supabase**, um serviço BaaS (Backend as a Service) gratuito para projetos de pequeno porte.

---

## ✅ Funcionalidades

- **Vitrine de produtos** — exibição de cards com imagem, nome, categoria e preço
- **Carrinho lateral** — adiciona e lista itens com atualização em tempo real
- **Autenticação completa via Supabase:**
  - Cadastro com confirmação por e-mail
  - Login e logout
  - Controle de sessão persistente
- **Proteção de compra** — apenas usuários autenticados podem finalizar pedidos
- **Finalização via WhatsApp** — gera mensagem automática com os itens do pedido e redireciona para o WhatsApp do vendedor
- **Design responsivo** — adaptado para mobile, tablet e desktop

---

## 🛠 Tecnologias

| Tecnologia | Uso |
|---|---|
| HTML5 | Estrutura da página |
| CSS3 | Estilização e responsividade |
| JavaScript (ES6+) | Lógica do carrinho e interações |
| [Supabase JS v2](https://supabase.com/docs/reference/javascript) | Autenticação de usuários |
| [Google Fonts](https://fonts.google.com/) | Tipografia (Cormorant Garamond + DM Sans) |
| [Unsplash](https://unsplash.com/) | Imagens dos produtos (demo) |

---

## 📦 Pré-requisitos

Não há dependências de instalação local. Você precisa apenas de:

- Um navegador moderno (Chrome, Firefox, Edge, Safari)
- Uma conta gratuita no [Supabase](https://supabase.com)
- Acesso ao seu número de WhatsApp Business (ou pessoal)

---

## 🚀 Como Usar

### 1. Clone o repositório

```bash
git clone https://github.com/seu-usuario/luminashop.git
cd luminashop
```

### 2. Configure o Supabase

Abra o arquivo `index.html` e localize o bloco de configuração no JavaScript:

```javascript
const SB_URL = "https://SEU-PROJETO.supabase.co";
const SB_KEY = "sua-chave-publica-aqui";
```

Substitua pelos valores do seu projeto Supabase. Veja a seção [Configuração do Supabase](#-configuração-do-supabase) para instruções detalhadas.

### 3. Configure o WhatsApp

No mesmo arquivo, localize e substitua o número pelo seu:

```javascript
const SEU_NUMERO_WHATSAPP = "5511999999999";
// Formato: código do país + DDD + número (sem espaços, hífens ou parênteses)
```

### 4. Abra no navegador

Por ser um arquivo HTML estático, basta abrir o `index.html` diretamente no navegador — ou hospedar em qualquer serviço de hospedagem estática (GitHub Pages, Vercel, Netlify, etc.).

---

## ⚙️ Configuração do Supabase

### Criando o projeto

1. Acesse [supabase.com](https://supabase.com) e crie uma conta gratuita
2. Clique em **"New Project"** e preencha as informações
3. Aguarde a criação do projeto (cerca de 2 minutos)

### Obtendo as credenciais

1. No painel do projeto, acesse **Settings → API**
2. Copie os valores:
   - **Project URL** → cole em `SB_URL`
   - **anon / public key** → cole em `SB_KEY`

> ⚠️ **Importante:** Use sempre a chave `anon` (pública). Nunca exponha a chave `service_role` em código front-end.

### Configurando a autenticação

1. Vá em **Authentication → Providers**
2. Certifique-se de que o provedor **Email** está habilitado
3. Em **Authentication → Email Templates**, você pode personalizar os e-mails de confirmação com a sua marca

### Habilitando confirmação de e-mail (opcional)

Por padrão, o Supabase exige confirmação de e-mail no cadastro. Para desativar em ambiente de testes:

1. Acesse **Authentication → Settings**
2. Desative a opção **"Enable email confirmations"**

---

## 🎨 Personalização

### Adicionando ou editando produtos

Localize o array `produtos` no JavaScript e edite conforme necessário:

```javascript
const produtos = [
    {
        id: 1,
        nome: 'Nome do Produto',
        categoria: 'Categoria',
        preco: 99.90,
        img: 'URL-da-imagem'
    },
    // adicione mais produtos aqui...
];
```

> 💡 Para imagens próprias, você pode hospedar no [Supabase Storage](https://supabase.com/docs/guides/storage) ou em qualquer CDN.

### Alterando cores e tipografia

As variáveis CSS ficam no início do arquivo, dentro do seletor `:root`:

```css
:root {
    --cor-primaria: #0f0f0f;       /* cor de fundo escuro, headers */
    --cor-secundaria: #f7f5f2;     /* cor de fundo da página */
    --cor-destaque: #c9a84c;       /* dourado — preços e destaques */
    --cor-botao: #0f0f0f;          /* cor dos botões principais */
    --cor-sucesso-bg: #25c26e;     /* botão de finalizar compra */
}
```

### Alterando o nome da loja

Substitua todas as ocorrências de `Lumina` no HTML pelo nome da sua loja.

---

## 📁 Estrutura do Projeto

```
luminashop/
│
├── index.html          # Arquivo principal — toda a aplicação está aqui
│                       # (HTML + CSS + JavaScript em arquivo único)
│
└── README.md           # Documentação do projeto
```

> O projeto foi desenvolvido intencionalmente como um único arquivo HTML para máxima simplicidade de implantação — sem build, sem dependências locais, sem servidor.

---

## 📸 Screenshots

| Vitrine | Carrinho com itens |
|---|---|
| *Tela inicial com os produtos em grid* | *Sacola lateral com resumo do pedido* |

> Adicione aqui suas capturas de tela reais após a configuração.

---

## 🌐 Deploy

O projeto pode ser publicado gratuitamente em qualquer uma dessas plataformas:

- **[GitHub Pages](https://pages.github.com/)** — ative em *Settings → Pages → Deploy from branch*
- **[Vercel](https://vercel.com/)** — importe o repositório e faça deploy em um clique
- **[Netlify](https://netlify.com/)** — arraste o arquivo HTML para o painel do Netlify

---

## 🤝 Contribuição

Contribuições são bem-vindas! Se quiser sugerir melhorias:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/minha-melhoria`)
3. Faça commit das suas alterações (`git commit -m 'feat: adiciona nova funcionalidade'`)
4. Envie para a branch (`git push origin feature/minha-melhoria`)
5. Abra um Pull Request

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

<p align="center">
  Feito com ♥ por <strong>Lumina Shop</strong>
</p>
