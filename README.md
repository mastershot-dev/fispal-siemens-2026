# Controle de Depoimentos — Fispal Tecnologia 2026 (Cliente: Siemens)

Relatório de entrega e instruções de publicação. Produzido por: Entrenova · Produção.
Última atualização: 17/06/2026.

---

## 1. Visão geral

Painel em HTML (arquivo único, sem dependências) para acompanhar as gravações do evento
**Fispal Tecnologia 2026** feitas para o cliente **Siemens**. Ele mostra, por dia de evento,
quem foi gravado, o status de cada depoimento (gravado → disponível no Drive → participante avisado)
e os links diretos para as pastas no Google Drive.

O objetivo é publicar este painel como uma página web (link permanente) para acompanhamento.

Arquivos desta entrega:

- `index.html` — o painel (é o arquivo que vai para o ar).
- `Controle_Depoimentos_Siemens.html` — cópia idêntica, para uso/edição interna.
- `README.md` — este documento.

---

## 2. Estrutura de pastas no Google Drive

O material bruto está organizado assim na pasta **BRUTO** (Google Workspace), já no padrão da agência:

```
BRUTO/
└── DIA 01/
    ├── DEPOIMENTOS/
    │   ├── DANIEL CASSIMIRO/   (5 vídeos + 1 áudio)
    │   ├── DIEGO CADETE/        (2 vídeos: bruto + edit)
    │   ├── DANIEL MARQUES/      (1 vídeo)
    │   └── RENAN/               (1 vídeo)
    ├── INSERTS/                 (23 vídeos)
    └── FOTOS/                   (2 fotos — Daniel Cassimiro)

DIA 02/
├── DEPOIMENTOS/
│   ├── BIANCA/                 (depoimento + insert — completo)
│   └── WILLIAM PEREIRA/        (multicam: CAM A, CAM B, INSERT — ainda subindo)
└── INSERTS/                    (em organização)
```

Os próximos dias (DIA 03 e DIA 04) seguirão o mesmo formato: cada dia com `DEPOIMENTOS`
(uma subpasta por pessoa) e `INSERTS`.

> **Acesso:** a pasta precisa estar compartilhada diretamente com a conta Google conectada
> (não apenas "qualquer pessoa com o link"), para que o conteúdo possa ser lido e os links atualizados.

---

## 3. Como o painel funciona

Todo o conteúdo é controlado por **duas listas no início do bloco `<script>`** dentro do
`index.html`. Não há banco de dados nem backend — basta editar essas listas e salvar.

**`PESSOAS`** — uma entrada por depoimento/insert:

```js
{ nome:"Daniel Cassimiro", role:"", dia:1, tipo:"Depoimento",
  status:"drive", drive:"https://drive.google.com/drive/folders/...", obs:"3 vídeos + áudio" }
```

Campos:

- `dia`: 1 a 4
- `tipo`: `"Depoimento"` ou `"Insert"`
- `status`: `"gravado"` (gravado, ainda não subiu) · `"drive"` (no Drive, falta avisar) · `"avisado"` (participante avisado)
- `drive`: link da pasta/arquivo no Google Drive (ou `""` se ainda não houver)
- `obs`: observação curta (opcional)

**`DIAS`** — rótulo e link da pasta de cada dia no Drive.

Os cartões de resumo no topo (total de pessoas, a subir, no Drive, avisados) e os filtros de
busca/status são calculados automaticamente a partir da lista `PESSOAS`.

---

## 4. Como publicar no GitHub Pages

1. Criar um repositório novo no GitHub. O GitHub Pages no plano gratuito serve a partir de
   repositório **público** — confirme que isso é aceitável para este conteúdo (ver seção 6).
2. Na página do repositório: **Add file → Upload files** e subir o `index.html`
   (opcionalmente também `README.md`). Confirmar o commit.
3. Ir em **Settings → Pages**.
4. Em **Source**, selecionar a branch `main` e a pasta `/ (root)`. Salvar.
5. Aguardar cerca de 1 minuto. A URL pública aparece no topo da seção Pages, no formato:
   `https://<usuario>.github.io/<nome-do-repo>/`
6. Essa URL é o link a ser enviado ao cliente.

### Alternativa rápida (sem repositório): Netlify Drop

Acessar `app.netlify.com/drop` e arrastar o `index.html`. O link é gerado na hora.
Para torná-lo permanente, criar uma conta gratuita e "reivindicar" o site.

---

## 5. Como atualizar depois da publicação

O painel é um **retrato do momento** (snapshot): não se atualiza sozinho. A cada novo dia,
nova pessoa ou mudança de status:

1. A Entrenova atualiza as listas `PESSOAS` / `DIAS` no `index.html`.
2. Sobe a nova versão do arquivo:
   - **GitHub:** substituir o `index.html` no repositório (novo commit) — o Pages republica sozinho.
   - **Netlify:** arrastar o arquivo novo novamente.

> Não fica "ao vivo" lendo o Drive porque uma página pública não pode acessar o Drive privado
> com segurança. A atualização é sempre por nova versão do arquivo.

---

## 6. Observações importantes

- **Link público:** qualquer pessoa com a URL conseguirá abrir a página. Como esta versão inclui
  os links das pastas de **material bruto**, quem tiver o endereço também alcança esse material.
  Se for preciso restringir, há a opção de gerar uma versão "somente status" (sem links do bruto).
- **Logo da Siemens:** carregada da Wikimedia Commons; há um texto de reserva ("SIEMENS") que
  aparece caso a imagem não carregue (ex.: sem internet).
- **Sem dependências:** o arquivo é autocontido (HTML + CSS + JS num só lugar); abre em qualquer
  navegador moderno, inclusive offline (exceto a logo e os links externos).

---

## 7. Referências (links do Drive)

- Pasta BRUTO: https://drive.google.com/drive/folders/1PL-kKBP-sAzmVu3oFlzM0JaocJBOM0cV

**DIA 01**
- DIA 01: https://drive.google.com/drive/folders/16b5L1mZy05sWZcg75hP_IHAM2omu0Nfc
- Depoimento — Daniel Cassimiro: https://drive.google.com/drive/folders/1SOnRYMIOrQH8seyal1ZLE_0ihBR2nOyd
- Depoimento — Diego Cadete: https://drive.google.com/drive/folders/1nur3qp0ULQ3-twydzXCZK4AzMsq1a0Hu
- Depoimento — Daniel Marques: https://drive.google.com/drive/folders/1LWZWGQKcPsp659qEvhSO2hvJUL3Cdqzp
- Depoimento — Renan Felipe do Valle: https://drive.google.com/drive/folders/1VCrA7BI5kr_N-yyo5bOqkmCM1KjhcZfg
- Inserts (23 vídeos): https://drive.google.com/drive/folders/1ujweaII9zHC0X_7BBIPxLGNjmrmVrG-u
- Fotos (2 fotos — Daniel Cassimiro): https://drive.google.com/drive/folders/18OiTFG1WRp-m38AC59tKDaC2J4AIyNLn

**DIA 02**
- DIA 02: https://drive.google.com/drive/folders/1eOC8gfhdbX7d0UyHf--0UI8sNf7aRFQo
- Depoimento — Bianca (completo): https://drive.google.com/drive/folders/1kzFhEANUbgR4mq1U7aoTAaO5goroD_Nd
- Depoimento — William Pereira (ainda subindo): https://drive.google.com/drive/folders/14XwRiXvRPsjNsg4l5SeWTAFS5a12X2Tl
- Inserts (em organização): https://drive.google.com/drive/folders/1bKNtFJeTKhOJhQJFH1Z55WW6qpUq7Yh3

---

## 8. Pendências do DIA 01 (encerrado)

O DIA 01 foi concluído. Itens de produção em aberto, registrados no painel:

- **Repórter por um dia (Vídeo 01)** — *a editar*. Notas de edição:
  - Entrada do evento: usar a tomada em que aparece escrito **"EXPOSITORES"** no topo (essa é a que vale).
  - Foram gravados **dois finais**; escolher junto com o editor qual ficou melhor.
- **Sistema VIC** (Cassimiro e Augusto) — *a subir no Drive*. Vídeo do sistema de verificação
  de qualidade (ex.: banana); material gravado, ainda não enviado.
