# Defesa Cibernética — SENAC Goiás

Portfólio acadêmico e repositório central dos laboratórios do curso **Técnico em Defesa Cibernética (SENAC Goiás / PMGO)**.

**Responsável:** Gabriel Silveira Lima  
**Conta GitHub deste projeto:** [@gabriel-silima](https://github.com/gabriel-silima)  
**Situação:** estrutura inicial de documentação; resultados práticos só serão marcados como concluídos após validação por evidências.

## Portfólio visual

Uma página estática responsiva foi criada em [`index.html`](index.html), pronta para publicação via GitHub Pages após ativação manual em Settings → Pages. Veja [como configurar](docs/configurar-github-pages.md). A publicação do Pages ainda não foi verificada.

## Organização

| Área | Conteúdo | Estado da documentação |
| --- | --- | --- |
| UC3 — Segurança física e lógica de redes | Inventário, análise de riscos, controle de acesso, segmentação | A documentar |
| UC4 — Programação com Python | Scripts e exercícios de desenvolvimento | A documentar |
| UC5 — Criptografia | Hashes, HMAC, integridade de arquivos e laboratórios Packet Tracer | [Roteiro de integridade](laboratorios/uc05-integridade-hash-hmac/README.md) |
| Redes e infraestrutura | VirtualBox, Linux, Windows, Wireshark, switches e VLANs | A documentar |
| Projetos integradores | Relatórios, testes, resultados e recomendações | A documentar |

## Projetos relacionados na mesma conta

- [Blitze Digital — PM-GO](https://github.com/gabriel-silima/BLITZE-DIGITAL---PM-GO) — repositório independente; conteúdo pendente de documentação.
- [Missão extra — classificador multiporta](https://github.com/gabriel-silima/-miss-o-extra-classificador-multi-porta) — repositório independente; conteúdo pendente de documentação.

> Os links acima apontam para repositórios existentes. Não representam comprovação de implementação ou conclusão das atividades.

## Padrão de documentação

Cada laboratório deve registrar:

1. **Objetivo e escopo** do exercício.
2. **Ambiente** (software, versão, máquinas, rede e topologia).
3. **Procedimento reproduzível**, com comandos e parâmetros.
4. **Resultados observados**, distinguindo esperado de efetivamente comprovado.
5. **Evidências sanitizadas**, com datas, capturas, hashes e arquivos próprios.
6. **Análise de riscos e contramedidas** (Blue Team).
7. **Conclusão e limitações**, sem inventar testes ou resultados.

## Segurança e privacidade

- Não incluir senhas, tokens, chaves privadas, arquivos `.env`, informações institucionais restritas ou dados pessoais reais.
- Sanitizar capturas, logs, endereços e nomes antes de publicar.
- Não redistribuir materiais integrais de professores, arquivos de atividade de terceiros ou laboratórios protegidos sem autorização.
- Arquivos de evidência bruta ficam fora do repositório público; publicar apenas trechos seguros e de autoria própria.

Veja [SECURITY.md](SECURITY.md), [guia de publicação](docs/guia-de-publicacao.md) e [análise de autenticação](docs/autenticacao.md).

---

*Projeto acadêmico de defesa cibernética. O registro de uma atividade no portfólio não implica sua execução ou aprovação sem evidência correspondente.*
