# Autenticação e autorização — repositório SENAC

## Escopo da análise

Este repositório foi inicializado como documentação/portfólio. Na inspeção inicial, estava vazio, sem aplicação, backend, middleware, endpoints de login, testes de autenticação ou documentação técnica de sessão. **Não há autenticação de uma aplicação própria para auditar aqui.**

A autenticação existente pertence à **plataforma GitHub**, que controla o acesso ao repositório. Não confundir isso com um login desenvolvido pelo projeto.

## Componentes e responsabilidades

| Componente | Papel |
| --- | --- |
| Pessoa usuária | Autentica-se no GitHub e concede permissões a ferramentas autorizadas |
| GitHub | Verifica identidade, autorização e permissões por repositório |
| Aplicação/integração GitHub conectada | Acessa recursos autorizados em nome da conexão selecionada, sem inserir credenciais neste código |
| Git/GitHub CLI (opcional, na máquina local) | Envia e recebe código via HTTPS autenticado ou SSH |
| Repositório | Armazena conteúdo e histórico Git; não guarda senha de usuário para autenticar commits |

## Fluxo de requisição — integração conectada

1. A pessoa autoriza a integração GitHub para a conta desejada.
2. A integração realiza uma requisição à API do GitHub no contexto da conta vinculada.
3. O GitHub verifica o token/credencial apresentado e as permissões correspondentes.
4. Se o acesso é autorizado, a API retorna dados ou aplica a alteração e registra o commit.

Nesta atividade, a conta vinculada selecionada para operações do portfólio foi `gabriel-silima` (SENAC). A conta `gsilveiralima` (Gran) não é destino das alterações deste projeto.

**Limite de visibilidade:** o código e a implementação interna da integração, o formato exato dos tokens, os escopos efetivos e seu armazenamento interno não estão disponíveis neste repositório. Não é possível inferi-los somente pela presença de uma conexão funcional.

## Fluxo local por Git (quando utilizado)

```text
Desenvolvedor -> git push -> HTTPS (Credential Manager/CLI) ou SSH (chave local)
              -> GitHub autentica -> verifica permissão de escrita -> recebe commits
```

Em HTTPS, a ferramenta de credenciais deve armazenar o mecanismo de autenticação de forma segura. Em SSH, a chave **privada** fica na máquina de origem e o GitHub reconhece a chave **pública** cadastrada. Nenhuma delas deve entrar no repositório.

### Verificações locais sugeridas (Windows/PowerShell)

```powershell
gh auth status
gh auth switch --user gabriel-silima
git remote -v
git config --local user.name
git config --local user.email
```

- `gh auth status`: verifica as contas autenticadas na GitHub CLI (se instalada).
- `gh auth switch`: seleciona a conta SENAC na GitHub CLI, caso já esteja autenticada nela.
- `git remote -v`: mostra o destino configurado para o repositório local.
- `git config`: mostra a identidade registrada nos commits; **não comprova** qual conta tem acesso de escrita.

A sessão do navegador, a conta vinculada no ChatGPT e a autenticação da GitHub CLI são contextos diferentes; selecionar uma não reconfigura automaticamente as outras.

## Tratamento de credenciais e tokens

- Não inserir token na URL remota Git, no código, em arquivos de configuração versionados ou em imagens de evidência.
- Usar credenciais de curta duração e permissões mínimas quando possível.
- Não registrar `Authorization`, cookies ou credenciais nos logs.
- Se a credencial for exposta, revogá-la e substituí-la; eliminar uma linha não a remove de commits antigos.
- Um nome/e-mail em `git config` é metadado de autoria, não uma senha nem prova de autenticação.

## O que falta para auditar login de uma aplicação?

Quando houver um aplicativo neste repositório, identificar os arquivos de rotas/controladores de login, middleware, provedores de identidade, cookies/sessões, bibliotecas JWT/OAuth, configuração de CORS/CSRF e testes. Somente então é possível desenhar o fluxo concreto de login e renovação/revogação de tokens com evidência do código.
