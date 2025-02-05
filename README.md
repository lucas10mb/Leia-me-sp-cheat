<h1>Leia-me Cheat</h1>

Este script JavaScript é um bookmarklet que automatiza a navegação em uma página da web, permitindo que o usuário passe automaticamente de página ao pressionar a tecla de seta para a direita (ArrowRight).

## Funcionalidades Principais

- **Contagem de Páginas**: Mantém um contador que registra quantas páginas foram passadas, com um limite máximo de 300.

- **Botões Interativos**:
  - **Iniciar**: Começa a navegação automática, solicitando ao usuário um intervalo em milissegundos para mudar de página. Se o valor fornecido for inválido, o padrão é 1000 ms.
  - **Parar**: Interrompe a navegação automática e limpa o contador.
  - **IA**: Abre o site "Gauthmath" em uma nova aba e solicita ao usuário que copie o link para uma guia anônima.
  - **Como Usar**: Abre um link com instruções sobre como usar o script.

- **Eventos de Teclado**: O script simula pressionamentos de tecla para navegar pelas páginas e pode interromper a navegação enviando um evento de tecla "Escape".

Os botões são criados dinamicamente e posicionados na tela, permitindo fácil acesso ao usuário. Mensagens de alerta informam o usuário sobre o status da execução e as ações realizadas.

<pre id="codigo">javascript:(function(){var count=0,maxTimes=300,intervalId,isRunning=false;function createButton(text,onClick,top){var button=document.createElement('button');button.textContent=text;button.style.position='fixed';button.style.top=top+'px';button.style.right='10px';button.style.zIndex='1000';button.style.padding='10px';button.style.backgroundColor=text==='Iniciar'?'#4CAF50':(text==='Parar'?'#F44336':'#FFC107');button.style.color='white';button.style.border='none';button.style.borderRadius='5px';button.style.cursor='pointer';document.body.appendChild(button);button.addEventListener('click',onClick);}function openIAInNewTab(){alert("Por favor, copie o seguinte link e cole em uma guia anônima:\n\nhttps://www.gauthmath.com/");window.open('https://www.gauthmath.com/','_blank');}function openHowToUse(){window.open('https://pastebin.com/raw/nHA4919C','_blank');}function startInterval(){isRunning=true;var intervalMillis=prompt("Em quantos milissegundos você quer passar de página? (Digite o valor em milissegundos)");intervalMillis=parseInt(intervalMillis,10);if(isNaN(intervalMillis)||intervalMillis<=0){alert("Valor inválido. O intervalo será definido como 1000 ms por padrão.");intervalMillis=1000;}var event=new KeyboardEvent('keydown',{key:'ArrowRight',code:'ArrowRight',keyCode:39,which:39,bubbles:true});intervalId=setInterval(function(){document.dispatchEvent(event);count++;console.log("Páginas passadas: "+count);if(count>=maxTimes){clearInterval(intervalId);alert("Terminou de passar as páginas!");isRunning=false;}},intervalMillis);}function stopInterval(){clearInterval(intervalId);isRunning=false;alert("Script parado!");var event=new KeyboardEvent('keydown',{key:'Escape',code:'Escape',keyCode:27,which:27,bubbles:true});for(var i=0;i<50;i++){setTimeout(function(){document.dispatchEvent(event);},10*i);}}createButton('Iniciar',function(){if(!isRunning){count=0;startInterval();}else{alert("O script já está em execução!");}},10);createButton('Parar',stopInterval,50);createButton('IA',openIAInNewTab,90);createButton('Como Usar',openHowToUse,130);})();</pre>

<a href="https://youtu.be/YHcdtNHDhHE?si=HPBZf3pjnZjoh-hV" target="_blank">Tutorial</a>


