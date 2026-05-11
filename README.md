# Radar Eleitoral · Deploy na Vercel

Pasta pronta pra publicar como site estático.

## Subir na Vercel — método rápido (drag & drop)

1. Acesse https://vercel.com/new
2. Clique em **"Browse all templates"** → role até embaixo → **"Other"** → **"Static"**
   Ou simplesmente arraste esta pasta inteira no painel da Vercel
3. Confirme o projeto (sem build command, output directory: `./`)
4. Deploy! Em ~20 segundos o site está no ar em `radareleitoral.vercel.app`

## Subir via CLI (mais rápido se já usa Vercel)

```bash
cd deploy
npx vercel --prod
```

Login, confirma o nome do projeto, pronto.

## Configurar o subdomínio `radareleitoral.nodedata.com.br`

### 1. Na Vercel
- Abra o projeto → **Settings → Domains**
- Adicione: `radareleitoral.nodedata.com.br`
- A Vercel mostrará o registro DNS necessário:
  ```
  Type:  CNAME
  Name:  radareleitoral
  Value: cname.vercel-dns.com
  ```

### 2. No Registro.br (painel do nodedata.com.br)
- Entre no painel → **DNS → Editar Zona**
- Adicione:

| Tipo  | Nome           | Dados                  | TTL  |
|-------|----------------|------------------------|------|
| CNAME | radareleitoral | cname.vercel-dns.com.  | 3600 |

⚠️ No Registro.br digite apenas `radareleitoral` (sem `.nodedata.com.br`) — ele completa sozinho.
⚠️ O ponto final no `cname.vercel-dns.com.` é importante em alguns painéis.

### 3. Aguardar
- Propagação DNS: 10 min a 2h
- Volte na Vercel → o domínio fica verde quando detecta
- SSL automático em ~1 min

Pronto: `https://radareleitoral.nodedata.com.br` no ar.

## Estrutura

```
deploy/
├── index.html         # página principal
├── tokens.css         # design tokens
├── vercel.json        # config de cache + clean URLs
└── assets/
    ├── cerebro.webp   # hero brain
    ├── logo-original.png
    └── demo/          # screenshots do fluxo WhatsApp
```
