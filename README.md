# iOS Web App

 * Descrição: Guia para o desenvolvimento de um aplicativo web para iOS.
 * Escrito por: Cassio A. Cardoso ([@cassiocardoso](https://twitter.com/cassiocardoso/)), Fernando A. Damião ([@fa_damiao](https://twitter.com/fa_damiao/))
 * Escrito em: 2012-12-12
 * Última alteração: 2013-01-24 12:36 por Fernando A. Damião


Este guia tem a intenção de demonstrar como transformar uma página em um Web App focando no S.O. móvel iOS.

Tudo o que é demonstrado aqui são basicamente meta tags que devem ser incluídas na sua página.

O guia parte do principio que a sua página foi desenvolvida seguindo técnicas de Responsive Design por se adaptar a diferentes dispositivos e resoluções.


## 'Enganando' o efeito zoom
Para o usuário ter uma melhor experiência ao acessar o seu Web App o conteúdo deve ser visualizado normalmente, ou seja, sem nenhum tipo de zoom, para isso você precisa definir o `viewport` inicial em 1.0 como no exemplo abaixo:

	<meta name="viewport" content="width=device-width, initial-scale=1.0">


## Transformando a sua página em um Web App

**Funciona no iOS 2.1 ou superior**

Para que a sua página possa ser utilizada como um Web App em dispositivos que utilizam iOS, utilize a meta tag abaixo:

	<meta name="apple-mobile-web-app-capable" content="yes">


## Definindo a barra de status

**Funciona no iOS 2.1 ou superior**

A barra de status é a barra de status exibida pelo sistema, mas existe a possibilidade de customização, os valores possíveis são:

 * default
 * black
 * black-translucent

Os valores devem ser alterados no atributo `content` da meta tag abaixo:

	<meta name="apple-mobile-web-app-status-bar-style" content="default">

**OBS:** Essa tag não funciona sem a utilização da meta tag `apple-web-app-capable` com o `content="yes"`.


## Definindo um nome para o aplicativo

**Funciona no iOS 6**

**OBS:** Procure dar um nome de até 12 caracteres para o seu App, ou o título será truncado.

Para definir um nome para o aplicativo, sem interferir no título da página, utilize a meta tag abaixo:

	<meta name="apple-mobile-web-app-title" content="MyApp">

**OBS2:** Caso essa tag não seja definida, por padrão o título do App será o título da página.


### Título para iOS 5 ou inferior
Em dispositivos que utilizam iOS 5 ou inferior a tag acima não funciona, o que significa que o título do aplicativo será o título da página, mas isso pode ser alterado com o código abaixo:

	<script type="text/javascript">
		if (navigator.userAgent.match(/iPhone|iPad|iPod/i)) {
			document.title = "MyApp";
		}
	</script>


## Definindo o ícone do aplicativo

**Funciona no iOS 1.1.3 ou superior**

**Suporte a múltiplas dimensões a partir do iOS 4.2 ou superior**

Esse ícone aparece na tela inicial do usuário, existe a necessidade de preparar ícones com dimensões para

Como os dispositivos suportam diversas resoluções precisamos fazer um ícone para cada um, abaixo estão às dimensões e os respectivos dispositivos.

 * 57x57 - iPhone
 * 72x72 - iPad
 * 114x114 - iPhone Retina Display
 * 144x144 - iPad Retina Display

Para exibir os ícones siga essa ordem:

    <link rel="apple-touch-icon-precomposed" sizes="144x144" href="apple-touch-icon-precomposed-144x144.png">
    <link rel="apple-touch-icon-precomposed" sizes="114x114" href="apple-touch-icon-precomposed-114x114.png">
    <link rel="apple-touch-icon-precomposed" sizes="72x72" href="apple-touch-icon-precomposed-72x72.png">
    <link rel="apple-touch-icon-precomposed" href="apple-touch-icon-precomposed-57x57.png">

**OBS:** Prefira fazer os ícones com border-radius de 10px, pois você terá uma noção maior de como ficará o icone em um dispositivo.


## Definindo uma 'startup image'

**Funciona no iOS 3 ou superior**

Essa imagem é exibida quando seu aplicativo está abrindo/carregando, abaixo estão às dimensões das imagens.

iPhone:

 * 320x460
 * 640x920 - Retina Display
 * 640x1096 - iPhone 5 Retina Display

iPad:

 * 768x1004 - Portrait
 * 1024x748 - Landscape
 * 1536x2008 - Portrait - Retina Display
 * 2048x1496 - Landscape - Retina Display

Para carregar as imagens você terá que usar todas as tags abaixo:

    <link rel="apple-touch-startup-image" href="apple-touch-startup-320x460.png" media="(device-width: 320px)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-640x920.png" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-640x1096.png" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-768x1004.png" media="(device-width: 768px) and (orientation: portrait)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-1024x748.png" media="(device-width: 768px) and (orientation: landscape)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-1536x2008.png" media="(device-width: 1536px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-2048x1496.png" media="(device-width: 1536px)  and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)">

**OBS:** Não são utilizadas as resoluções máximas, pois temos que considerar a status bar que consome 20px em dispositivos normais e 40px em dispositivos com Retina Display.


**OBS2:** Essa tag não funciona sem a utilização da meta tag `apple-web-app-capable` com o `content="yes"`.


## Desabilitar o reconhecimento automático de telefones

**Funciona no iOS 1 ou superior**

Para impedir que telefones sejam transformados em links que chamam os números utilize a meta tag abaixo:

	<meta name="format-detection" content="telephone=no">


## Balão para instalar o Web App
Para indicar que a página pode ser instalada como um aplicativo existe o plugin jQuery [add2home](https://github.com/cubiq/add-to-homescreen), ele possui a aparência exata do iOS e possui suporte para diversas línguas e algumas customizações.

Abaixo está um exemplo de como utilizar o add2home:

	<link type="text/css" rel="stylesheet" href="add2home.css">
	<script type="text/javascript">
		var addToHomeConfig = {
			animationIn: 'fade',
			animationOut: 'fade',
			lifespan: 20000,
			touchIcon: true,
			message:'pt_br'
		};
	</script>
	<script type="text/javascript" src="add2home.js"></script>

**OBS:** A configuração do plugin deve ficar antes de carregar, isso é uma recomendação do próprio desenvolvedor e pode ser vista [aqui](http://cubiq.org/add-to-home-screen).


## Exemplo completo
Este exemplo transforma a sua página em um Web App para iOS para todos os dispositivos e com balão para adicionar como aplicativo.

**OBS:** Cuidado com a utilização da tag base.

	<meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="default">
    <meta name="format-detection" content="telephone=no">
    <meta name="apple-mobile-web-app-title" content="MyApp">
    <link rel="apple-touch-icon-precomposed" sizes="144x144" href="apple-touch-icon-precomposed-144x144.png">
    <link rel="apple-touch-icon-precomposed" sizes="114x114" href="apple-touch-icon-precomposed-114x114.png">
    <link rel="apple-touch-icon-precomposed" sizes="72x72" href="apple-touch-icon-precomposed-72x72.png">
    <link rel="apple-touch-icon-precomposed" href="apple-touch-icon-precomposed-57x57.png">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-320x460.png" media="(device-width: 320px)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-640x920.png" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-640x1096.png" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-768x1004.png" media="(device-width: 768px) and (orientation: portrait)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-1024x748.png" media="(device-width: 768px) and (orientation: landscape)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-1536x2008.png" media="(device-width: 1536px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)">
    <link rel="apple-touch-startup-image" href="apple-touch-startup-2048x1496.png" media="(device-width: 1536px)  and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)">
    <link type="text/css" rel="stylesheet" href="add2home.css">
    <script type="text/javascript">
        if (navigator.userAgent.match(/iPhone|iPad|iPod/i)) {
            document.title = "MyApp";
        }
        var addToHomeConfig = {
            animationIn: 'fade',
            animationOut: 'fade',
            lifespan: 20000,
            touchIcon: true,
            message:'pt_br'
        };
    </script>
    <script type="text/javascript" src="add2home.js"></script>


## Referências
Esses Links ajudaram a entender sobre o assunto e a escrever esse guia:

 * [Safari HTML Reference: Supported Meta Tags](https://developer.apple.com/library/safari/#documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html)
 * [Safari HTML Reference: Configuring Web Applications](https://developer.apple.com/library/safari/#documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)
 * [iOS Web App Icons & Startup Images](http://taylor.fausak.me/2012/03/27/ios-web-app-icons-and-startup-images/)
 * [iPhone 5 Web App Startup Image](http://taylor.fausak.me/2012/09/20/iphone-5-web-app-startup-image/)
 * [iOS web app icons & startup images](https://gist.github.com/2222823)
 * [Stack Overflow - Mulitple “apple-touch-startup-image” resolutions for iOS web app (esp. for iPad)?](http://stackoverflow.com/a/10011893)
 * [Enabling Startup Image for an iPad Web Application](http://www.amirnaor.com/?p=71)
 * [Stack Overflow - What can I do to prevent iPhone 4 from cutting off my title when adding to home screen?](http://stackoverflow.com/a/4883846)
