# **Como o computador lê o código**
### **Linguagem de alto nível**
- Entendíveis por humanos
- Código fonte

---
### **Código de maquina**
- Entendíveis por computadores
- Código binário
  1. Em um computador, cada um desses **0s e 1s** é chamado de **bit**, que vem do inglês "**Binary Digit**" ou dígito binário. Essa é a menor unidade possível para o armazenamento de informação.
  2. Como **bit** é uma unidade muito pequena, costuma-se trabalhar com grupos de **8 bits**, essa quantidade agrupada de bits é chamada de **byte**. Por convenção, quando medimos o armazenamento em um computador usamos o byte.
  3. Para representar essas unidades, utilizamos **b** (“b” minúsculo) para o bit e **B** (“B” maiúsculo) para byte. Ou seja, 1B = 8b.
  4. Você pode encontrar essas unidades em conjunto com [prefixos SI](https://pt.wikipedia.org/wiki/Prefixos_do_Sistema_Internacional_de_Unidades) como `kg`(quilograma, ou mil unidades de gramas), `M`(mega, ou 1 milhão de unidades), `G` (giga, ou 1 bilhão de unidades) e assim por diante. Por exemplo:
      * Um arquivo de **200 MB** é um arquivo com **200 milhões de bytes**.
      * Uma internet com velocidade de **20 Mbps** transfere **20 milhões de bits por segundo** ou **2,5 milhões de bytes por segundo**.

---
### **Compiladores**
1. Lê linha a linha do código fonte e traduz(compila) para código de máquina
2. Execução rápida
3. Verifica erros antes de executar
4. Executa apenas na máquina que compilou o código ou com componentes similares
5. Para o programa ser executado diretamente pelo computador, ele precisa ser escrito como código de máquina.
6. Um compilador junta todo o código traduzido de uma vez. Assim, ele pode ser executado diretamente pelo computador.
    ~~~c
    C
    ~~~
    ~~~rusty
    Rusty
    ~~~
    ~~~go
    GO
    ~~~

---
### **Interpretadores**

1. Interpreta os comandos em tempo real de execução
2. Execução lenta
3. Verifica erros após execução
4. Executa em diferentes máquinas
    ~~~javascript
    JavaScript
    ~~~
    ~~~python
    Python
    ~~~
    ~~~ruby
    Ruby
    ~~~

    ~~~php
    PHP
    ~~~

---
### ****************************************************************Uma mesma linguagem pode ser "compilada" ou "interpretada"****************************************************************

1. Jit complilation
2. JVM
   * Byte code

---
---
# **Como um computador executa um programa**
### **Memoria não volátil ou Memória secundária**

Não apaga os dados ao desligar o computador

1. **HD (Hard Disk)+**
    1. Discos magnéticos
    2. Grande capacidade de armazenamento
    3. Baixo custo
    4. Processamento de dados lento
2. **SSD (Solid State Drive)**
    1. Chips eletrônicos
    2. Tamanho menores
    3. Maior velocidade no processamento de dados
    4. Custo alto
    5. Limitação de escrita
    6. A velocidade de um SSD, em comparação ao HD, pode acelerar a inicialização do computador e de programas. Como não há a necessidade de uma grande capacidade de armazenamento, o SSD possui um bom custo-benefício.
3. **ROM (Read-Only Memory)**
    1. **Atenção: um HD ou SSD não são ROMs! Essa é uma confusão comum, principalmente porque todos são não-voláteis.**
    2. No **SSD** ou **disco rígido** é onde são armazenadas informações sobre o sistema operacional do seu computador e permite você utilizá-lo no dia a dia. Mesmo assim, no momento que o computador liga, como ele sabe quais dispositivos estão conectados nele e onde ele precisa ler as informações?
        1. Esse tipo de dado inicial e crucial para o funcionamento do computador é localizado na memória **ROM**, do inglês ”**Read-Only Memory”** ou “**memória de apenas leitura”**. Ela é um tipo de memória **não-volátil** com baixo armazenamento, bem diferente da **RAM** ou **HD/SSD**. Uma ROM possui vários modelos, mas todos são projetados para serem apenas lidos, ou seja, não é esperado que o usuário escreva informações nessa memória.
        2. Dessa forma, quando o computador é inicializado, as primeiras informações que ele irá buscar estarão na ROM, por exemplo, a **BIOS**
         ( **Basic Input/Output System** ou **sistema básico de entrada/saída**). Elas vão ajudá-lo a identificar os dispositivos conectados, como o HD, e carregar o sistema operacional.

---
### **Memória volátil ou Memória de trabalho**

Os dados são apagados ao desligar o computador

1. **RAM (Random Access Memory)**
    1. Da mesma forma que uma bancada maior permite fazer várias receitas ao mesmo tempo, uma RAM com grande capacidade permite o uso de vários programas juntos. Com isso, o computador não vai ficar tão lento quando abrir várias abas do navegador.

---
### **Processador ou CPU** (Central Process Unit)

A CPU são divididas em 3 partes principais

1. As instruções são processadas num ciclo de três passos chamados **buscar, decodificar e executar**
    1. **Clock**
        1. 3GHz (3 bilhões de tiques por segundos)
        2. Cada instrução passa por esse ciclo e o tempo entre cada uma é sincronizado pelo **clock** do processador.
        3. O clock define a velocidade com que as instruções são executadas. Ou seja, quanto maior a velocidade do clock, mais rápido um programa será executado.
        4. A velocidade do clock é um dos principais fatores para medir a velocidade de execução de um certo programa. Muitos entusiastas utilizam a técnica de [**overclocking**](https://pt.wikipedia.org/wiki/Overclocking)
         , que aumenta o desempenho em programas mas pode causar [**superaquecimento do processador**](https://pt.wikipedia.org/wiki/Superaquecimento_do_processador)
        , um maior gasto energético e uma redução no seu tempo de vida.
    2. **Registradores**
        1. O processador armazena dados em seus registradores. Lá são guardadas informações como a **instrução atual**, **valores intermediários em contas** e a **posição na memória da próxima instrução**.
        2. Buscar
    3. **(UC)** Unidade de controle
        1. Antes de serem executadas, as instruções precisam ser decodificadas pela **(UC)** Unidade de Controle 
        2. É a **UC** mesmo que é responsável por decodificar uma instrução lida na RAM. Cada bit decodificado liga um fio ou circuito específico que modifica o estado do processador.
    4. **(ULA)** Unidade Lógico Aritmética
        1. A **ULA** é apenas responsável pela execução de algumas instruções. Ela não decodifica as instruções.

---
---
# **Como um computador executa vários programas**
### Processadores modernos

1. Pipeline de instruções
    1. Possibilidade de aumentar a quantidade de instruções por ciclo
2. Lei de **********Moore**********
    1. Em 1965, Gordon Moore previu que o número de componentes de um circuito integrado (transistores) dobraria a cada período de 18 meses, resultando num processador duas vezes mais rápido. Isso originou a chamada Lei de Moore. Essa lei virou uma medida econômica das empresas e é responsável pelo crescimento exponencial de performance da tecnologia que vemos nas últimas décadas.
    2. Entretanto, nos últimos anos, os fabricantes de processadores estão encontrando limites físicos para manter esse padrão e o crescimento está [cada vez diminuindo mais](https://www.uol.com.br/tilt/noticias/redacao/2019/01/29/o-que-e-a-lei-de-moore-e-porque-voce-deve-se-preocupar-com-o-fim-dela.htm). Por isso, pesquisadores procuram outras soluções para manter o crescimento da performance de um processador, mas sem precisar aumentar o número de transistores ou a velocidade de clock.
    3. Algumas das soluções para isso são técnicas que você viu em aula. Outras são o uso de hardwares específicos que aceleram o processamento (aprenderemos sobre o assunto nas próximas atividades) e alterações na performance das linguagens de programação.

---
---
### **Input/Output**

1. **Drivers de dispositivo**
    1. permitem escrevermos o mesmo código para diversos dispositivos diferentes.
    2. São os drivers de dispositivo que abstraem as particularidades de cada dispositivo. Dessa forma, a gente pode escrever um código que desenha algo na tela e isso funcionará para vários monitores diferentes.
    3. O **disco rígido**, bem como o **SSD**, é um dispositivo de entrada e saída. Ele realmente guarda informações sobre o SO e, por isso, é um dos primeiros dispositivos que o computador procura na hora de ser [iniciado](https://www.tecmundo.com.br/aumentar-desempenho/11266-como-funciona-o-boot-de-um-computador.htm)
---
2. **Monitores**
    1. **Placa de vídeo:**
        1. Uma **GPU** (*Graphics Processing Unit*) ou **placa de vídeo** é a unidade responsável pela renderização dos pixels na tela do computador e está em todos os computadores pessoais. O [artigo da Oficina da Net](https://www.oficinadanet.com.br/hardware/27791-o-que-e-a-placa-de-video)
         traz uma ótima explicação se você tem interesse em saber mais sobre o assunto.
        2. Além disso, esse tipo de unidade de processamento é muito usado hoje em dia para diversas aplicações fora do escopo gráfico. Algoritmos de *machine learning*
         e ciência de dados utilizam a alta capacidade de processamento numérico da GPU para acelerar seus cálculos. Isso é chamada de **computação acelerada via GPU**
         e você pode conferir mais sobre o assunto no [artigo da Ciência e Dados](http://www.cienciaedados.com/gpu-e-deep-learning/)
        3. Por fim, para o ramo de *machine learning*
        , foi criada uma nova unidade para acelerar a computação: a **TPU**(*Tensor Processing Unit* ou Unidade de Processamento de Tensores). Elas aumentam muito a performance nessas aplicações, em relação à GPU, e é usada em grandes empresas de tecnologia. Você pode conferir a ideia no [vídeo da Google sobre TPU](https://www.youtube.com/watch?v=MXxN4fv01c8)
         (em inglês com legendas traduzidas para português pelo YouTube). Trata-se de uma tecnologia bem complexa, então não precisa se preocupar em como ela funciona internamente.
        4. Como telas atuais possuem milhões de pixels, computadores pessoais precisam de placas de vídeo **(GPUs)** para **renderizar** eles a tempo para quem está usando.
        5. Placas de vídeo são especialistas em realizar tarefas repetitivas, simples e em grande quantidade ao mesmo tempo, como o cálculo de vários pixels da tela. Muitas delas são instaladas com o processador e são chamadas de ***placa de vídeo integrada***
        6. Dedicadas
---
3. **Teclado**
    1. O sinal, é baseado na posição do caractere. Dessa forma, cada tecla pode mudar seu significado sem precisar trocar o teclado. Tente mudar o idioma do seu teclado e veja o que acontece.

---
---
# **Como a memória funciona?**
### **Memória CACHE**

A memória cache é uma técnica muito importante para otimizar o funcionamento do processador e é cada vez mais explorada atualmente. Mesmo assim, essa não é uma ideia limitada aos componentes do processador mas é usada em quase todas as comunicações de dados atualmente.

Alguns lugares muito comuns são em navegadores, banco de dados e servidores.

A memória cache é usada para facilitar a comunicação do processador **(e registradores)** com a **memória RAM**. Por outro lado, você poderia pensar que a própria RAM ou um SSD (numa arquitetura mista) seriam os responsáveis por facilitar a comunicação com HD.

1. ****Cache em navegadores****
    1. Quando você acessa páginas em um navegador, como Chrome ou Firefox, você precisa se comunicar com servidores pela internet e esperar todo o conteúdo da página ser transferido para seu computador. Como as páginas não costumam ser alteradas com frequência, os navegadores costumam guardar esses dados dentro do próprio computador. Dessa forma, a próxima vez que você acessar ela, será muito mais rápido.
    2. Esse tipo de armazenamento local de dados de servidores também é usado em outros aplicativos, além de navegadores, como o Facebook.
2. ****Cache em bancos de dados****
    1. Alguns sistemas usam estruturas chamadas de bancos de dados. Elas são formas de guardar e estruturar uma grande quantidade de informação no **HD/SSD**. Porém, algumas pesquisas nessa estrutura podem não ser tão rápidas e seria interessante guardar valores muito pedidos para acelerar as respostas.
    2. Por isso, muitos bancos de dados utilizam uma estrutura de dados rápida (muitas vezes em memória RAM) para guardar essas respostas, como o [Memcached](https://aws.amazon.com/pt/memcached/) e o [Redis](https://aws.amazon.com/pt/redis/). Você pode encontrar [cursos aqui na Alura sobre Redis](https://cursos.alura.com.br/course/nosql-chave-valor-com-redis-1/task/9498).
3. ****Cache em servidores****
    1. Muitas vezes, alguns serviços de um servidor podem ser bem mais requisitados que outros. Por exemplo, uma página inicial de um site de computadores que mostra todos os produtos em desconto naquele dia. Dessa forma, para acelerar a resposta e diminuir a carga nas máquinas, esses equipamentos podem guardar versões prontas dessas páginas durante um período de tempo. Assim, sempre que uma pessoa pedir a página para o servidor, ele não precisará buscar no banco de dados nem fazer um processamento complexo para devolver a resposta.
    2. Esse processo é normalmente feito em conjunto com uma **Content Delivery Network** (CDN) ou Rede de Distribuição de conteúdo. Elas basicamente distribuem cópias das suas mídias para diversos servidores para que o dado esteja o mais próximo possível de você. Essa é a técnica vital para o [funcionamento da Netflix](https://exame.com/tecnologia/este-e-o-segredo-da-netflix-para-nunca-sair-do-ar/). Você pode ver mais sobre como elas funcionam no [vídeo do Código Fonte TV](https://www.youtube.com/watch?v=02rvd_7HcFY).
4. **Programas cache-friendly**
    1. Algumas linguagens que oferecem um controle maior na alocação de memória, como C e C++, podem ter o tempo de execução de seus programas influenciados pela memória cache. Ou seja, só mudando a ordem de execução de alguns trechos de código, ele pode ficar bem rápido ou lento. Programas que conseguem otimizar o máximo isso são chamados de ***cache-friendly*** ou bons para o cache.
    2. Para ver isso funcionando na prática, acesse o [código no GitHub](https://gist.github.com/AndrewIjano/5a46dfd50693dd2d198266b0f864b738)
     e [execute aqui](http://cpp.sh/).
    3. Você vai ver que o tempo de execução sem cache é muito maior:
    4. Isso acontece porque essa segunda execução não é feita de forma linear. Assim, quando o computador for copiar um bloco de dados para o cache, o próximo elemento da nossa lista nunca vai estar lá.
    5. Para visualizar o que está acontecendo, a animação abaixo ilustra a execução de cada um, caso tivéssemos uma lista de 8 elementos.
    6. De qualquer forma, não são todas as implementações de linguagens que precisam desse cuidado com o cache. O Node.js, uma implementação de JavaScript, faz várias otimizações que quase mascaram esse tipo de coisa. Mesmo assim, é algo importante para se ter em mente ao longo de uma carreira de programação.

### **Hierarquia de memória**

Memórias rápidas são muito caras, então não é viável usá-las para armazenar uma grande quantidade de dados.

Como o princípio da localidade diz que nós usamos a mesma porção de dados durante um período de tempo, é importante ter memórias rápidas para poucos dados e lentas para muitos dados.

Nós costumamos acessar sempre uma mesma porção de dados durante um período de tempo. Por isso, temos várias camadas de memória com capacidades e velocidades diferentes. Dessa forma, a região pequena que vai ser mais acessada vai estar numa memória mais rápida que outros dados numa região mais abrangente.

**“+ Velocidade”  TOPO**

1. **Registradores**
    1. Os registradores são a memória mais rápida de um computador, podendo ser acessados em um ciclo de clock!                                        ****
    2. 1 Ciclo de clock           ~500 Bytes       
2. **Níveis de cache**                                          
    1. Cache L1 700GB/s        64KB
    2. Cache L2 200GB/s        500KB
    3. Cache L3 150GB/s        4MB
3. **Armazenamento**
    1. RAM        10GB/s          8GB
        1.  A RAM guarda dados muito utilizados vindos do HD ou SSD. ****
    2. SSD          2GB/s           500GB
    3. HD           200MB/s       4TB    
4. **CLOUD           2MB/s          PB ou EB**

**“+ Armazenamento” RODA PÉ**

1. DRAM
2. SRAM

### Princípio da localidade

1. **Localidade Temporal**
    1. Significa que se eu acessei nesse lugar recentemente eu vou querer acessar de novo em breve e esse é o princípio de quando se está fazendo um programa e vou usar sempre as mesmas variáveis.
    2. Sempre vou usar aquela mesma posição da memória, se eu tenho as minhas pastas, os meus arquivos e eu separo essas pastas por ano, a pasta onde estão os meus projetos provavelmente só vou acessar a pasta que vai falar dos projetos que eu estou realizando naquele ano.
    3. Quando pasta dos outros anos serão  menos acessadas e da mesma forma tem o segundo princípio da localidade, que é a localidade espacial que significa que se eu acessei aqui, vou acessar o vizinho em breve.
2. **Localidade espacial**
    1. É aquela mesma ideia que usamos para fazer a cópia da memória, a cópia dos dados para a memória Cache, acessei essa instrução e vou em copiar um bloco inteiro, porque eu vou querer acessar as próximas instruções que vão vir logo abaixo.
    2. Isso acontece porque os programas que executa são feitos de forma sequencial, os dados que armazena são feitos de forma sequencial - são as listas por exemplo que são valores um ao lado do outro. Esse princípio da localidade faz com que a hierarquia de memória faça sentido.
    3. Em período de tempo vamos acessar sempre a mesma porção de memória muito mais, uma mesma porção de memória do que qualquer outra coisa do computador, por isso se aquela mesma porção da memória coloca na memória mais rápida que der.

### **Fitas magnéticas**

Pode parecer estranho ouvir falar no uso de fitas magnéticas hoje em dia. Esse tipo de tecnologia ficou muito popular entre os anos de 1970 e 1990 para o armazenamento de áudio, com as **fitas cassetes**, mas quase não se ouve mais falar delas com a chegada de novas tecnologias de armazenamento.

Mesmo assim, as fitas magnéticas nunca chegaram a desaparecer e elas possuem uma enorme demanda no mundo todo, mas em uma área diferente do que você espera.

1. Uma das grandes desvantagens das fitas magnéticas é que elas são [muito lentas para ler e escrever](https://youtu.be/alxqpbSZorA?t=492)! A coisa complica mais se você precisa fazer o acesso aleatório de dados, porque a máquina precisaria rebobinar toda a fita para conseguir ir de um ponto da memória até outro. Por isso, elas foram facilmente substituídas por HDs e SSDs no uso diário em computadores pessoais.
2. Por outro lado, fitas magnéticas podem armazenar enormes quantidades de dados por um preço baixo e possuem um tempo de vida bem alto. [Estimativas de 2016 da Forbes](https://www.forbes.com/sites/tomcoughlin/2016/07/24/the-costs-of-storage/?sh=4ae7ff763239)
 mostram que HDs são 65% mais caros que fitas. Além disso, você pode encontrar [fitas com 12 TB](https://www.lto.org/lto-8/) de capacidade (e, a partir de 2030, podem aparecer [modelos com 400 TB](https://gizmodo.uol.com.br/fita-armazenamento-fujifilm-400tb/)). Ainda, fitas tem um [tempo de vida de até 30 anos](https://cbltech.com.br/blog/vantagens-e-desvantagens-de-se-utilizar-fitas-magneticas-para-backup-de-dados.html#:~:text=Estima%2Dse%20que%2C%20em%20condi%C3%A7%C3%B5es,dependendo%20da%20forma%20de%20grava%C3%A7%C3%A3o), 6 vezes maior que um HD.
3. Esse é o cenário perfeito para momentos em que precisamos armazenar grandes quantidades de dados que vamos mexer muito raramente: os backups. Muitos dados no mundo são armazenados em fitas, como física de partículas, arquivos nacionais, [grandes filmes](https://spectrum.ieee.org/computing/it/the-lost-picture-show-hollywood-archivists-cant-outpace-obsolescence) e até bancos. [Neste vídeo](https://www.youtube.com/watch?v=z4DP0Lg-qpw) , você pode ver como a Organização Europeia para a Pesquisa Nuclear (CERN) utiliza fitas para armazenar os 1 GB por segundo de dados que eles captam em pesquisas.

### **Processador de 32 ou 64 bits**

Tamanho de informação que pode ser processada na CPU em um ciclo de clock

Quantidade de informação em largura que pode ser armazenado dentro de um registrador

1. **Processador 32bits**
    1. 2³²
    2. Valor equivalente a 4GB e não é possível ultrapassar mais que esses 4GB
2. **Processador 64bits**
    1. 2^64
    2. Aproximadamente 16 Bilhões de GB

---
---
# **Como os dados são armazenados?**
### Números inteiros

Para serem armazenados são verificados os bits armazenados

**********bits********** começados com [ 0 ] são bits positivos

********bits******** começados com [ 1 ] São bits negativos

Sendo assim os 8 bits  equivalem a 255 valores de -127(negativo) a 127(positivo)

1. Na linguagem **C** por exemplo um número inteiro precisa de ************4Bytes************ para ser representado, o que equivale a +/- 2Bilhões

### Caracteres

1. **ASCII** (American Standard Code for Information Interchange)
    1. Padrão de 7 bits
2. **Latin1**
    1. Caracteres acentuados
    2. Mais símbolos
3. **Unicode**
    1. Só números
4. **UTF-8**
    1. Não existe um número fixo de bytes
    2. Os caracteres são de tamanhos variados
    3. Vimos a codificação UTF-8 para representar os vários caracteres do sistema Unicode, mas essa não é a única codificação para isso. Existem outros dois sistemas UTF-16 e UTF-32. Vamos ver a diferença entre esses três.
        1. Atenção: todos os três sistemas conseguem codificar todos os caracteres do Unicode. Apenas a quantidade de bits que eles usarão para fazer isso que muda.
    4. Essa codificação representa os caracteres em pedaços de **8 bits** e sua grande vantagem é manter os textos codificados apenas em ASCII (a grande maioria da Web no passado) intactos. Ele tem um tamanho variável e cada caractere pode ocupar 8, 16, 24 ou 32 bits.
    5. Essa é a codificação mais comum na web hoje.
5. ****UTF-16****
    1. Essa codificação representa os caracteres em pedaços de **16 bits**. Isso significa que a codificação não é mais compatível com ASCII e ocupa o dobro de memória em textos que possuem apenas caracteres da língua inglesa. Ele tem um tamanho variável e cada caractere pode ocupar 16 ou 32 bits.
    2. Sua grande vantagem é ocupar menos espaço quando o texto possui muitos caracteres asiáticos (UTF-8 usaria 3 bytes por caractere e UTF-16 apenas 2). Mesmo assim, essa vantagem é [bem questionada](http://utf8everywhere.org/) e muitas pessoas não recomendam o seu uso em muitos casos.
    3. Essa é a [codificação usada em sistemas Windows](https://docs.microsoft.com/pt-br/windows/win32/intl/unicode?redirectedfrom=MSDN).
6. **UTF-32**
    1. Essa codificação representa os caracteres em pedaços de **32 bits**. Ela não é compatível com ASCII e ocupa **4 vezes** mais espaço em textos que só utilizavam ASCII. Mesmo assim, diferentemente do UTF-8 e UTF-16, essa codificação tem um **tamanho fixo** e essa é sua grande vantagem. Como cada caractere ocupa a mesma quantidade de bits, é fácil saber em qual posição cada caractere está em um texto (é só pegar o índice do caractere e multiplicar por 32).

### Ponteiros

Valores que apontam para outros valores da memória são chamados de ponteiros e é dessa forma de organizar que representa valores complexos no computador.

1. Quando se faz a cópia do conteúdo de lista1 para lista 2, na verdade estamos fazendo a cópia é da referência para o conteúdo da lista 1, na lista1 tem um ponteiro para o conteúdo.
2. Está apontando para uma região da memória onde estão os valores e quando faz a cópia disso faz também cópia para apontar para o mesmo endereço da memória, por isso faz a modificação - elemento de índice zero da lista dois também modifica o elemento zero da lista1.
3. Porque eles estão apontando para os lugares, estão modificando o mesmo elemento, por isso que quando está trabalhando com listas e objetos que trabalham usando ponteiros, tem que ter muito cuidado ao fazer cópia dos elementos.

### **Passagem por referência**

1. Como na variável está passando com um argumento da função uma referência para variável e o valor da variável, assim mesmo modificando qualquer coisa dentro da função, não vai alterar a variável fora.
2. Stefany vai fazer aniversário e, para isso, ela decidiu criar um programa em **JavaScript**
 que mexe com idades.
    1. Primeiro, ela fez uma função `calculaProximaIdade()`, que recebe a idade que ela tem agora e imprime quantos anos ela terá depois do aniversário. 
    2. Em seguida, ela criou a função `calculaProximasIdades()`, que recebe a lista de idades dela e de seus amigos e devolve quantos anos todos terão ao final do ano. 
    3. Por fim, ela fez uma função `calculaIdadesDaqui5Anos`, que recebe a mesma lista de antes mas devolve as idades que todos terão daqui cinco anos. 
    4. O programa ficou da seguinte forma:
        
        ```jsx
        function calculaProximaIdade(idade) {
            idade += 1;
            console.log(idade);
        }
        
        function calculaProximasIdades(idades) {
            for (let i = 0; i < idades.length; i += 1) {
                idades[i] += 1;
            }
            console.log(idades);
        }
        
        function calculaIdadesDaqui5Anos(idades) {
             for (let i = 0; i < idades.length; i += 1) {
                idades[i] += 5;
            }
            console.log(idades);
        }
        
        const idadeStefany = 21;
        calculaProximaIdade(idadeStefany);
        
        const idadesAmigos = [idadeStefany, 20, 23, 18, 7];
        calculaProximasIdades(idadesAmigos);
        
        calculaIdadesDaqui5Anos(idadesAmigos);
        ```
        
    5. A segunda função modifica o valor da variável `idadesAmigos`
    6.  Assim, a última função vai mostrar `[ 27, 26, 29, 24, 13 ]`, todos com exatamente um ano a mais que o esperado.
    7. Listas são passadas por referência para funções. Dessa forma, se modificamos seu conteúdo dentro da função, a lista é modificada. Por outro lado, isso não acontece com número, que são passados por valor. Sabendo disso, tente arrumar o programa de Stefany e teste o resultado!
    8. O código tem um pequeno problema e isso está relacionado a alguma função ter seu argumento passado por referência, ou seja, se modificar dentro da função, modifica seu valor fora também.
    9. Os números são passados por valor como argumentos na função, ou seja, a variável original não tem seu valor modificado. Isso acontece da mesma forma com listas?
    10. Os números são passados por valor como argumentos na função, ou seja, a variável original não tem seu valor modificado. Isso acontece da mesma forma com listas?

### Imagem e áudio

Sabemos como armazenar tipos primitivos, como inteiros, caracteres e listas, mas como funcionam os tipos de dados que trabalhamos no dia a dia como imagens e áudio?

1. Imagens podem ser representadas como uma lista de três componentes **RGB (vermelho, verde e azul)**, onde cada componente vai representar um pixel.
2. O [vídeo do code.org](https://www.youtube.com/watch?v=15aqFQQVBWU) explica de forma bem ilustrada como elas são armazenadas e como aplicamos filtros nelas. Além disso, alguns formatos não armazenam imagens dessa forma. Formatos como JPEG realizam a compressão de uma imagem e você pode ver como isso funciona no [vídeo do Leo Isikdogan](https://youtu.be/Ba89cI9eIg8)
3. Para áudio, a ideia é semelhante. Áudios são propagados como ondas, então podemos capturar a altura que a onda está em certos períodos de tempo, isso dá um número, e guardamos em uma lista de alturas. Você pode ver uma explicação mais detalhada disso no [vídeo do Computerphile](https://www.youtube.com/watch?v=1RIA9U5oXro)

### Notação científica

### Número de ponto flutuante

Podemos representar números muito grandes usando a representação de ponto flutuante. Essa representação tem um grande ganho em eficiência, mas causa erros de arredondamento.

[1 bit = Sinais] [8 bits = Expoente] [23 bits = Coeficiente]

1. Mesmo assim, se você programa com a linguagem Python, verá que você pode representar números gigantescos, como dois elevado a mil, sem erros de arredondamento. (Você pode testar isso no [interpretador online de Python](https://www.python.org/shell/). )
2. Como, então, ele consegue armazenar números tão grandes? Ele usa mais de 1000 bits para armazenar todos os seus números? A resposta para isso é: **Inteiros de precisão arbitrária.**
    1. Essa técnica, também chamada de ***BigInteger*** ou ***Bignum***, armazena números sem restrição de posição. A ideia é, em vez de fixar a mesma quantidade de bits para representar todos os números, utilizar uma quantidade variável.
    2. Isso pode ser feito guardando cada dígito do número numa lista e as contas são realizadas dígito a dígito, como aprendemos na escola. Para otimizar, as implementações não usam a nossa base decimal (dígitos de 0 a 9) mas uma base de 2^30 (“dígitos” de 0 a 2^30 - 1). Com isso, as operações dígito a dígito são feitas como operações de inteiros convencionais.
3. Dessa forma, não há uma restrição para o tamanho que esses números podem ter (além do limite de memória que o seu computador deve ter para armazenar tudo isso). Por isso, é dito que esses números tem precisão arbitrária. [Várias linguagens](https://en.wikipedia.org/wiki/List_of_arbitrary-precision_arithmetic_software) possuem implementações desse tipo de número mas, diferente do Python, costumam ser bibliotecas auxiliares da linguagem.
4. De qualquer forma, se um ***Bignum*** tem precisão infinita por que não usamos ele como o padrão para tudo? Isso acontece porque fazer contas com ele é muito lento. Quanto mais dígitos o número tiver, mais computações vai demorar para fazer todos os cálculos. Além disso, não precisamos de uma precisão tão extrema na maioria das aplicações práticas. Por isso, os números de precisão arbitrária são bem importantes mas não podem ser aplicados em qualquer situação.
5. Se você quer saber mais sobre o assunto, você pode ler o [artigo, um pouco avançado, do Arten Golubin](https://rushter.com/blog/python-integer-implementation/) (em inglês) sobre a implementação do **Bignum** em Python. Lá tem vários detalhes de implementação e é destrinchado como algumas contas são feitas.
6. Cada linguagem de programação usa essas ideias de forma diferente. Por exemplo, em JavaScript, todos os números são representados pelo tipo [Number](https://developer.mozilla.org/pt-BR/docs/Glossario/N%C3%BAmero), que é um número de ponto flutuante de 64 bits. Ou seja, ela não possui tipos numéricos de números inteiros como outras linguagens.