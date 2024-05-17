# Para saber mais: tipos de WAF

Vimos no vídeo que o WAF funciona como um proxy reverso, mas como será que ele pode ser implementado? Para isso, existem 3 tipos de WAF:

### WAFs de rede

Normalmente é um hardware instalado localmente, como o fabricado pela [Barracuda](https://www.barracuda.com/products/webapplicationfirewall). Para o seu gerenciamento, em geral é oferecido um serviço de segurança com opções de configurações.

![alt text: Hardware em formato de paralelepípedo na cor preta, com a logo em azul da Barracuda no canto superior esquerdo. Logo ao lado há duas entradas de cabo ethernet, uma wan e outra lan. No canto superior direito, há um painel de luzes led vermelha, verde e amarela.](https://caelum-online-public.s3.amazonaws.com/2698-seguranca-defensiva/01/aula1-img1.png)

### WAFs de host

WAF baseado em software que traz como vantagem uma maior possibilidade de personalização com um custo baixo. Entretanto, ele possui algumas desvantagens, como o consumo de recursos do servidor local, a complexidade da implementação e os custos de manutenção.

### WAFs na nuvem

Os WAFs hospedados na nuvem geralmente são administrados pelos provedores do serviço. É uma opção fácil de implementar e oferecida em modelo de assinatura, mas sua desvantagem é transferir a responsabilidade de administrar a ferramenta para terceiros.

Para mais informações, confira esse exemplo de [solução de WAF na nuvem da Cloudflare](https://www.cloudflare.com/pt-br/waf/).
