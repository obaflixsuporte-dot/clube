# Clube de Estudo Bíblico

Mesmo código da área de membros do curso: site estático + funções na Vercel, sem banco de dados e sem build. Tema escuro por padrão.

## Materiais e acesso

Os materiais ficam em `content/cursos.json`, cada um com sua pasta em `content/<id>/`.

- `"gratis": true`: liberado para qualquer pessoa que entrar com um e-mail.
- `"produtos"`: IDs dos produtos da Cakto que liberam o material (a assinatura do clube e o produto avulso daquele material).
- `"checkout"`: link de compra mostrado no botão "Quero liberar" de quem não tem o material.

Antes de publicar, troque `ID_ASSINATURA_CLUBE` e os `ID_AVULSO_...` pelos IDs reais da Cakto.

## Adicionar um material novo

1. Crie a pasta `content/<id>/` com `media/estudo.pdf` (e `media/audiobook.mp3`, se tiver).
2. Crie `content/<id>/modulos.json` e `content/<id>/aulas/<id>-ler.md` copiando de outro material.
3. Adicione o material em `content/cursos.json`.

Na aula, `<div class="leitor" data-pdf="media/estudo.pdf"></div>` abre o leitor (lembra a página) e `<audio controls preload="none" src="media/audiobook.mp3"></audio>` abre o player (velocidade e retomada).

## Rodar no computador

```
node dev.mjs     # http://localhost:5180
```

Com `DEV_MOCK=1`, a Cakto é simulada: os e-mails em `DEV_PAID` compraram os produtos em `DEV_PRODUCTS`.

## Variáveis na Vercel

`SESSION_SECRET`, `CAKTO_CLIENT_ID`, `CAKTO_CLIENT_SECRET` e, para donos/equipe, `EMAILS_LIBERADOS`.
