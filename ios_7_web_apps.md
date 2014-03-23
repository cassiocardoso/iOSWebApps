# iOS 7 Web Apps

## Licença

O guia está licenciado sob [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/) ![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png).

O que significa que você pode baixar, utilizar (desde que o uso não seja comercial) e até distribuir desde que sejam citados os autores.

Se sinta livre para alterar/modificar o guia, mas para isso você precisa manter a mesma licença.

Saiba mais sobre a licença Creative Commons na (excelente) tirinha do [Nerdson/Hacktoon](http://labs.hacktoon.com/docs/creative-commons/).

## Tópicos

 * [TL;DR](#tldr)
 * [Tamanho dos Ícones](#tamanho-dos-ícones)
 * [Video Track](#video-track)
 * [&lt;progress>](#progress)
 * [Remoção do suporte ao &lt;datetime>](#remoção-do-suporte-ao-datetime)

## TL;DR

Está com pressa? Não quer ler o texto completo, segue um resumo das principais modificações:

 * **Mudanças na UI (_User Interface_):** Coloração da _toolbar_; problemas com a navegação em tela cheia; novas medidas para os ícones; a tag _<title>_ no iPhone não fica mais visível na página; possível conflito com novos gestos.
 * **Novos Dispositivos:** Nada de novo para eles, continua tudo como era para o iPhone 5.
 * **HTML 5:** video track, `<progress>`, **REMOÇÃO** do suporte a `<input type="datetime">`.
 * **HTML 5 APIs:** Page Visibility, AirPlay API, melhoramentos no canvas, **REMOÇÃO** de suporte para Shared Workers, Web Speech Synthesis API, unprefixed Web Audio e Animation Timing.
 * **CSS:** Regions, Sticky position, FlexBox, ClipPath, unprefixed Transitions e outros melhoramentos.
 * **Home Screen Webapps:** Web View Pagination, JavaScript runtime para aplicativos nativos e novas habilidades para o player de vídeo.

## Tamanho dos Ícones

Os novos ícones do iOS 7 estão 5% maiores em relação às versões anteriores, por exemplo, nos iPhones com tela Retina eles medem agora 120x120 pixels, contra os 114x114 de anteriormente.

Os ícones de sistema também adotaram o _flat design_ e agora não possuem mais o efeito de brilho presente nos iOS antigos.

Os novos tamanhos de ícones disponíveis no iOS 7 são:

 * iPhone / iPod Touch Retina: 120x120 pixels
 * iPad 2 / iPad Mini: 76x76 pixels
 * iPad Retina: 152x152 pixels

**NOTA:** Devemos nos lembrar que o iOS 7 não está disponível para nenhum iPhone que não possua _retina display_, por isso se não disponibilizarmos os novos tamanhos o aparelho carregará automaticamente o ícone relativo do iOS 6.

A tabela abaixo relaciona os tamanhos de ícones que devem ser definidos para cada versão de iPhone, iPod Touch e iPad disponíveis atualmente:

```html
<!-- non-retina iPhone pre iOS 7 -->
<link rel="apple-touch-icon" href="icon57.png" sizes="57x57">
<!-- non-retina iPad pre iOS 7 -->
<link rel="apple-touch-icon" href="icon72.png" sizes="72x72">
<!-- non-retina iPad iOS 7 -->
<link rel="apple-touch-icon" href="icon76.png" sizes="76x76">
<!-- retina iPhone pre iOS 7 -->
<link rel="apple-touch-icon" href="icon114.png" sizes="114x114">
<!-- retina iPhone iOS 7 -->
<link rel="apple-touch-icon" href="icon120.png" sizes="120x120">
<!-- retina iPad pre iOS 7 -->
<link rel="apple-touch-icon" href="icon144.png" sizes="144x144">
<!-- retina iPad iOS 7 -->
<link rel="apple-touch-icon" href="icon152.png" sizes="152x152">
```

## Video Track

O elemento `<video>` agora suporta um filho chamado `<track>` que pode ser utilizado para inserir legendas aos vídeos. Há suporte para várias linguagens e elas aparecerão em um seletor dentro do _player_ de vídeo, possibilitando ao usuário trocar as legendas ou desativá-las.

Os únicos tipos de _tracks_ suportadas são `caption` e `subtitle`, eles são definidos utilizando o atributo `kind`. Um atributo **obrigatório** é o `srclang` onde devemos definir, no padrão [ISO](http://en.wikipedia.org/wiki/ISO_639-1) qual a linguagem da legenda.

As legendas são úteis quando um usuário pode ouvir o áudio, mas não entende a linguagem. Já os _captions_ são úteis quando o usuário não pode ouvir o áudio, ele inclui informações adicionais como: _música de fundo tocando_.

```html
<video>
    <source src="video.mp4">
    <track kind="captions" src="caption-en.vtt" srclang="en">
    <track kind="subtitles" src="subtitle-rr.vtt" srclang="br">
</video>
```
## &lt;progress>

O elemento `<progress>` agora é suportado. Ele pode ser usado para criar uma barra de progresso na página baseado em dois atributos: `max` e `value`.

```html
<progress max="100" value="50">
```

## Remoção do suporte ao &lt;datetime>

Seguindo o exemplo do Chrome o Safari no iOS agora também não suporta mais o elemento `<input type="datetime">` e irá interpretá-lo como um `<input type="text">`.
