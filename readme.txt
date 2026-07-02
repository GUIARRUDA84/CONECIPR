# Protocolo de Intenções Digital — CONECI-PR

Página única (`index.html`) para adesão ao Protocolo de Intenções do Conselho Estadual de
Controle Interno do Paraná. As adesões são gravadas num **Google Forms** (→ planilha) e a
página é compartilhada por **link no WhatsApp**. Não precisa de servidor: é hospedagem estática.

---

## Passo 1 — Criar o Google Forms (o "banco de dados")

1. Acesse **forms.google.com** → formulário em branco. Título: `Adesões CONECI-PR`.
2. Crie **9 perguntas**, todas do tipo **"Resposta curta"**, nesta ordem:
   1. Município
   2. Poder
   3. Órgão / UCCI
   4. Titular
   5. Cargo
   6. E-mail
   7. Telefone
   8. Equipe fundadora (recebe "Sim"/"Não")
   9. Frentes de contribuição
3. Em **Respostas**, clique no ícone de planilha para gerar a planilha vinculada (seu registro).

## Passo 2 — Pegar os códigos dos campos (`entry.XXXX`)

1. No editor do formulário (aba **Perguntas**), menu **⋮ (Mais)** no canto superior direito →
   **"Preencher formulário"**. (Antigamente chamava-se "Obter link pré-preenchido"; a Google renomeou.)
2. O formulário abre para preenchimento. Digite um valor qualquer em cada campo
   (ex.: `teste1`, `teste2`…) → clique em **"Gerar link"** → no topo, **Copiar**.
3. Cole o link num bloco de notas. Ele terá vários trechos assim:
   `entry.1234567=teste1&entry.7654321=teste2...`
4. Anote qual `entry.XXXXXXX` corresponde a cada campo (pela ordem/valores que você digitou).
5. Pegue também o **ID do formulário**: está na URL, entre `/d/e/` e `/viewform`.

> Se "Preencher formulário" não aparecer: confirme que você está na aba **Perguntas** (modo de
> edição, não na pré-visualização) e que o formulário já tem as perguntas criadas e salvas.

## Passo 3 — Preencher o bloco CONFIG no `index.html`

Abra `index.html`, encontre o bloco **CONFIG** (perto do fim) e ajuste:

- `GFORM_ACTION`: troque `COLE_SEU_ID_AQUI` pelo ID do formulário. Deve terminar em `/formResponse`.
- `GFORM_ENTRIES`: troque cada `entry.111111...` pelos códigos reais do Passo 2.
- `WHATSAPP_COORDENACAO`: número que recebe avisos, formato `55` + DDD + número (só dígitos).
- `LINK_DESTA_PAGINA`: o endereço público (você terá após o Passo 4).

> Enquanto o `GFORM_ACTION` não for configurado, o botão "Aderir" cai automaticamente para o
> WhatsApp, para nenhuma adesão se perder durante os testes.

## Passo 4 — Publicar (escolha UMA opção)

### Opção A — GitHub Pages (simples e gratuito)
1. Crie um repositório em **github.com** (ex.: `coneci-pr`).
2. Envie o arquivo `index.html` (botão "Add file" → "Upload files").
3. **Settings → Pages** → em "Branch" escolha `main` / pasta `/root` → **Save**.
4. Em ~1 minuto sai o link: `https://SEU-USUARIO.github.io/coneci-pr/`.

### Opção B — Vercel (gratuito, deploy em segundos)
1. Acesse **vercel.com** e entre com a conta do GitHub.
2. **Add New → Project** → importe o repositório `coneci-pr` → **Deploy**.
3. O link sai pronto (ex.: `https://coneci-pr.vercel.app`). Dá para ligar um domínio próprio depois.

### Opção C — Google Sites (sem GitHub)
Use quando não houver TI à mão: incorpore o HTML via **Inserir → Código incorporado**.
(É a opção mais limitada; prefira A ou B se possível.)

## Passo 5 — Voltar e finalizar o link

Depois de publicar, copie o endereço final, cole em `LINK_DESTA_PAGINA` no `index.html` e
republique. Pronto: mande o link no grupo de WhatsApp das UCCI.

---

## Como testar
- Abra o link no celular, preencha e toque em **Aderir**. Confira se a linha apareceu na planilha.
- Ative **"Quero construir o CONECI-PR desde o início"** e veja se marca `Sim` + as frentes.

## Observações
- Sem servidor e sem senhas: o Google Forms cuida do armazenamento.
- Para um painel por região, use os recursos de gráfico do próprio Google Sheets sobre a planilha.
