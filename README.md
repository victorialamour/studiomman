# Studio M'man

Site do Studio M'man, estúdio de sites sob medida para profissionais que vivem de reputação.

Uma página só, sem dependência de build: é abrir o `index.html` e funciona.

## Como rodar

Abrir o `index.html` no navegador já mostra a página. Para testar o vídeo e as imagens do jeito que o navegador vai tratar em produção, vale subir um servidor simples:

```bash
npx serve .
```

## Estrutura

```
index.html        a página inteira, com o CSS e o JavaScript embutidos
assets/
  sphere.mp4      a esfera de vidro do hero, 1920x1080
  capa.jpg        primeiro quadro do vídeo, usado como poster e na prévia do link
  proj-ribeiro.jpg
  proj-lamoure.jpg
  retrato.jpg
  lais.jpg
  hewerton.jpg
```

Está tudo num arquivo só de propósito. São 67 KB de HTML com o estilo e os scripts dentro, sem nenhuma biblioteca externa. Menos partes para quebrar e nada para instalar antes de publicar.

## Decisões que não são óbvias no código

**Tipografia.** Uma família só, Outfit, a mesma do logotipo. A hierarquia vem de peso e entreletra, não de trocar de fonte. Títulos de seção em caixa alta com peso 300 e entreletra 0.17em, que é o tratamento do brandboard.

**O rosa tem duas variáveis.** `--rosa` (#E6AFC1) é decorativo e só serve para preenchimento, porque sobre o papel off-white ele rende 1,7:1 de contraste. Para texto e anel de foco existe `--rosa-texto` (#9E4C66), que rende 5,3:1 e passa em AA. Nunca usar o primeiro em texto.

**Três estados de tema.** O site segue o sistema do visitante por padrão. O botão no menu grava a escolha dele e um script no `<head>` aplica antes da página desenhar, para não piscar na cor errada.

**O texto do hero tem largura limitada.** A coluna não passa de 560px porque, onde o scrim acaba, a borda escura da esfera derruba o contraste para 1,16:1. Foi medido.

**Nada de mix-blend-mode na camada de grão.** Uma camada fixa que mistura com a tela inteira força o navegador a recompor tudo, e em algumas placas de vídeo isso faz imagem e vídeo sumirem.

**Movimento some sozinho.** Cursor, botão magnético e palavra que gira só existem onde há mouse de verdade, e tudo respeita `prefers-reduced-motion`.

## O que ainda falta

- Print do site da @bylasiloja nos Projetos: o depoimento mais forte da página é dela, e a loja não aparece no portfólio
- Endereço dos sites publicados nos cartões de Projetos, hoje apontando para o Instagram
- A `og:image` está com caminho relativo. Ao publicar em domínio próprio, trocar para o endereço absoluto, senão o WhatsApp não acha a imagem da prévia
