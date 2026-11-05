# Política de segurança do portfólio

## Escopo

Este é um repositório **público** de documentação acadêmica. É inadequado para armazenar credenciais, informações operacionais reais ou evidências contendo dados pessoais.

## Não publicar

- Tokens GitHub, chaves de API, senhas, cookies de sessão, chaves SSH privadas ou arquivos `.env`.
- Dados de pessoas, informações internas de corporações, endereços de redes reais e outros identificadores sensíveis.
- Capturas de tráfego não anonimizadas; arquivos de laboratório de terceiros sem autorização de redistribuição.
- Dumps de bancos de dados, malware executável, credenciais de simulação desnecessárias.

## Controles recomendados

1. Inspecionar `git status`, `git diff --cached` e os arquivos antes de qualquer commit.
2. Usar .gitignore, mas não confiar somente nele: arquivos rastreados continuam sujeitos a commit.
3. Preferir exemplos de dados sintéticos, capturas censuradas e relatórios resumidos.
4. Guardar segredos em gerenciadores locais ou recursos próprios de secrets e usar tokens com escopo mínimo e expiração.
5. Ativar MFA na conta GitHub e revisar permissões das aplicações conectadas.
6. Em caso de publicação acidental, **revogar e rotacionar o segredo imediatamente**; remover do commit atual não apaga o histórico.

## Evidências e resultados

Toda observação deve indicar se é **executada e verificada**, **pendente** ou apenas **resultado esperado**. Não atribuir hash, sucesso de teste, arquivo alterado ou captura a uma execução que ainda não ocorreu.
