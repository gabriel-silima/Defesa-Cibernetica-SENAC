# UC5 — Verificação da integridade de arquivos com MD5 e HMAC

**Status:** roteiro documentado; execução e resultados ainda não registrados neste repositório.

## Objetivo

Verificar alterações de arquivos em uma topologia simulada no Cisco Packet Tracer, comparar hashes MD5 com valores de referência e gerar um HMAC-SHA256 para autenticar a integridade de um arquivo.

## Ambiente do roteiro da atividade

- Cisco Packet Tracer, com cenário distribuído entre **Branch Office** e **HQ**.
- **Laptop BR-1** (Mike): consulta páginas internas de simulação e recupera seis arquivos por FTP.
- **HQ-Laptop-1** (Sally): recebe para investigação o arquivo suspeito.
- **HQ-Laptop-2** (Bob): contém o arquivo financeiro usado no exercício de HMAC.
- **CSE-LABVM** (VirtualBox): terminal com `md5sum` e `openssl`.

Os nomes `branch.corp` e `hq.corp` referem-se à rede **simulada do Packet Tracer**, não a serviços reais de internet.

## Parte 1 — Recuperação dos arquivos

1. No Laptop BR-1, abrir `http://branch.corp` no navegador do Packet Tracer.
2. Consultar os hashes de referência informados na página de referência do exercício; registrar a fonte exata exibida no cenário.
3. No Prompt de Comando do Laptop BR-1, iniciar `ftp hq.corp` e autenticar-se com as credenciais **de laboratório fornecidas pelo instrutor**.
4. Executar `dir` no servidor FTP e baixar, com `get <nome>`, os arquivos abaixo:

```text
NEclients.txt
NWclients.txt
Nclients.txt
SEclients.txt
SWclients.txt
Sclients.txt
```

5. Encerrar o FTP com `quit`, executar `dir` localmente e verificar a presença dos seis arquivos.

Não publicar credenciais de laboratório, capturas que contenham senhas, dados originais do cliente ou arquivos protegidos por direitos de terceiros.

## Parte 2 — Conferência de hashes

Conforme o roteiro didático, copiar o conteúdo do arquivo em um terminal Linux e calcular:

```bash
echo -n 'CONTEUDO_EXATO_DO_ARQUIVO' | md5sum
```

Quando o arquivo original estiver disponível no próprio Linux, é preferível calcular diretamente seus bytes:

```bash
md5sum NEclients.txt
```

**Atenção:** quebras de linha, espaços finais, codificação e a opção `-n` alteram os bytes submetidos ao hash; os dois métodos só são comparáveis quando usam exatamente os mesmos bytes.

Registrar os hashes de referência e os calculados, identificar arquivos divergentes **somente depois de conferir o resultado real**, e comunicar a suspeita a Sally pelo mecanismo de e-mail simulado do Packet Tracer.

| Arquivo | Hash de referência | Hash calculado | Comparação |
| --- | --- | --- | --- |
| NEclients.txt | Pendente | Pendente | Não verificada |
| NWclients.txt | Pendente | Pendente | Não verificada |
| Nclients.txt | Pendente | Pendente | Não verificada |
| SEclients.txt | Pendente | Pendente | Não verificada |
| SWclients.txt | Pendente | Pendente | Não verificada |
| Sclients.txt | Pendente | Pendente | Não verificada |

Depois da confirmação, Sally deve recuperar o arquivo suspeito no HQ-Laptop-1 para análise. Não identificar previamente o arquivo alterado sem observação.

## Parte 3 — HMAC-SHA256

No cenário simulado, localizar o arquivo financeiro de Bob em HQ-Laptop-2, copiar seu conteúdo de modo fiel para CSE-LABVM e gerar o HMAC com OpenSSL, usando apenas a chave de teste fornecida no roteiro:

```bash
openssl dgst -sha256 -hmac 'CHAVE_DE_TESTE' rendimentos.txt
```

**Divergência a verificar no material recebido:** a denominação do arquivo varia entre `income.txt`, `redimentos.txt` e `rendimentos.txt`. Confirmar qual nome realmente existe no dispositivo antes de executar o comando. Não alterar a extensão ou presumir o conteúdo.

### MD5 versus HMAC

- **MD5**: identifica diferenças acidentais entre bytes quando há uma referência confiável, mas não é seguro contra adversários capazes de criar colisões.
- **HMAC-SHA256**: combina função hash com chave secreta; permite verificar integridade e autenticidade para quem compartilha a chave. Não criptografa o conteúdo.
- Uma correspondência de HMAC com o valor de referência só pode ser afirmada após calcular ambos sob a **mesma chave e o mesmo conteúdo**.

## Evidências a registrar depois da execução

- Captura da topologia (sem informações sensíveis).
- Listagem dos arquivos recebidos no Laptop BR-1.
- Tabela de hashes comparados com a referência.
- Identificação do arquivo divergente e justificativa.
- Registro do envio à supervisora na simulação.
- Resultado do HMAC e comparação com a referência, com a chave mascarada.
- Medidas defensivas sugeridas: algoritmos modernos, controle de acesso, trilhas de auditoria e proteção dos backups.

## Critério de conclusão

O laboratório será marcado **Validado** quando as três partes forem realizadas no Packet Tracer/CSE-LABVM, as respostas estiverem respaldadas por valores de hash efetivos, e as evidências estiverem documentadas de forma segura. Até lá, **nenhum resultado foi presumido**.
