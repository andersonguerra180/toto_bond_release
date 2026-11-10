<p align="center">
  <img src="assets/icone.png" width="128" alt="Ícone do Totó-Bond">
</p>

<h1 align="center">Totó-Bond</h1>

<p align="center">
  Junta pastas e <code>.zip</code> fragmentados numa pasta só, confere tudo com SHA-256 e conversa com o Google Drive.<br>
  <b>Windows e Mac.</b>
</p>

<p align="center">
  <a href="https://github.com/andersonguerra180/toto_bond_release/releases/latest"><b>⬇️ Baixar a versão mais nova</b></a>
</p>

---

## Qual arquivo baixar

Na página do [release mais novo](https://github.com/andersonguerra180/toto_bond_release/releases/latest), em **Assets**:

| Seu computador | Arquivo |
|---|---|
| **Windows** 10/11 (64 bits) | `Toto-Bond-Setup-<versão>-windows-x64.exe` |
| **Mac com Apple Silicon** (M1, M2, M3, M4…) | `Toto-Bond-<versão>-mac-apple-silicon.dmg` |
| **Mac Intel** | `Toto-Bond-<versão>-mac-intel.dmg` |
| Mac Intel, versão nativa (leve, ~4 MB) | `Toto-Bond-<versão>-mac-nativo-intel.zip` |

> Não sabe qual é o seu Mac? Menu  → **Sobre Este Mac**. Se aparecer "Chip Apple M…", é Apple Silicon; se aparecer "Processador Intel…", é Intel.

## Como instalar

### Windows

1. Baixe o `.exe` e abra.
2. O Windows deve mostrar **"O Windows protegeu o computador"** (SmartScreen), porque o instalador não tem assinatura paga. Clique em **Mais informações → Executar assim mesmo**.
3. Siga o instalador. Pra atualizar, feche o app e instale a versão nova por cima.

### Mac (`.dmg`)

1. Abra o `.dmg` e arraste o **TotoBond** para a pasta **Aplicativos**.
2. Na primeira vez, clique no app com o **botão direito → Abrir → Abrir** (o app não é notarizado pela Apple).
3. Se o Mac disser que o app **"está danificado e não pode ser aberto"** (comum em Apple Silicon), abra o **Terminal** e rode:
   ```bash
   xattr -cr /Applications/TotoBond.app
   ```
   Depois abra de novo.

### Mac nativo (`.zip`)

É a versão escrita em Swift, a mesma lógica num app bem menor. Ela é feita para Mac Intel e roda em Apple Silicon pelo Rosetta. Descompacte, mova o **Totó-Bond** para Aplicativos e abra com **botão direito → Abrir**.

## O que ele faz

### 🧩 Mesclar
Arraste as pastas e/ou os `.zip` (por exemplo, os vários `.zip` que o Google Drive gera num download grande) e clique em mesclar.

- **Dentro da 1ª pasta** (padrão): tudo é **movido** para dentro da primeira pasta da fila, sem gastar espaço com cópia. Se as pastas estiverem em discos diferentes, o app copia, confere o SHA-256 e só depois remove a origem.
- **Pasta nova:** cria `<nome>_merge` ao lado e **copia** tudo, sem mexer nas originais.
- **Nada é sobrescrito, nunca.** Arquivo repetido (mesmo caminho e mesmo conteúdo) é pulado. Arquivo com o mesmo nome e conteúdo diferente: os dois ficam, e o segundo ganha `(conflito - <origem>)` no nome.
- No fim saem `_relatorio.txt` e `_checksums.sha256`, e o `_duplicatas_por_conteudo.txt` quando houver arquivos idênticos em lugares diferentes (SHA-256 + tamanho + duração batendo 100%). As duplicatas só são apontadas, nunca apagadas.

### 🔍 Comparar
Compare uma pasta pronta com os fragmentos originais (`.zip`/pastas) e veja se **100% dos checksums batem**, com relatório do que falta, do que sobra e do que está diferente.

### ☁️ Google Drive
- **Enviar/mesclar** uma pasta do computador numa pasta do Drive: envia 4 arquivos por vez, pausa e retoma, e oferece continuar se o app fechar no meio. Não apaga nem sobrescreve nada no Drive.
- **Comparar** uma pasta do computador com uma pasta do Drive (SHA-256 + tamanho).
- **Informações** de uma pasta do Drive: quantidade de arquivos, tamanho, tipos, maiores arquivos e pontos de atenção.

#### Primeiro login no Google Drive
Na aba **Drive**, o app abre o navegador pra você entrar na sua conta Google. Como o app ainda não passou pela verificação do Google, pode aparecer a tela **"O Google não verificou este app"**:

1. Clique em **Avançado**.
2. Clique em **Acessar Totó-Bond (não seguro)**.
3. Autorize o acesso ao Google Drive.

O app usa só a API oficial do Google Drive. O login fica salvo apenas no seu computador; nada passa por servidor nosso.

### 🛡️ Feito pra não perder arquivo
- Nomes com acento (ex.: "Roda dos Orixás") extraídos do jeito certo, inclusive de `.zip` do Google Drive.
- Arquivos do zip com nomes que o disco acha iguais (acento composto × decomposto, maiúsculas × minúsculas) não se sobrescrevem: viram `nome (variante N)`, com aviso.
- Qualquer arquivo que possa não ter chegado ao destino aparece em **amarelo**, no alerta final e no topo do relatório.

## Conferir o download (opcional)

Cada release traz um `SHA256SUMS.txt`. No Mac/Linux:
```bash
shasum -a 256 -c SHA256SUMS.txt
```
No Windows (PowerShell):
```powershell
Get-FileHash .\Toto-Bond-Setup-*-windows-x64.exe -Algorithm SHA256
```

## Sobre este repositório

Aqui ficam só os instaladores prontos de cada versão, na aba [Releases](https://github.com/andersonguerra180/toto_bond_release/releases). Problemas e sugestões podem ir em [Issues](https://github.com/andersonguerra180/toto_bond_release/issues).
