# Mini Aula: Teoria dos Números e a Criptografia RSA

1. Contextualização Histórica da Criptologia
A criptologia, a ciência por trás da proteção de informações, é uma disciplina muito antiga, remontando ao sistema de escrita hieroglífica dos egípcios, há quase quatro mil anos. Ao longo dos séculos, líderes militares e governantes buscaram formas eficientes de comunicação sigilosa para proteger segredos e estratégias contra forças inimigas.
Em tempos mais recentes, a criptologia se tornou crucial. Se a Primeira Guerra Mundial foi a guerra dos químicos e a Segunda Guerra Mundial foi a guerra dos físicos, é dito que uma Terceira Guerra Mundial seria a guerra dos matemáticos, pois estes controlam a próxima grande arma: a informação. Matemáticos têm sido responsáveis tanto pelo desenvolvimento de códigos de proteção militar quanto pela tentativa de decifrá-los.
O avanço tecnológico, especialmente durante e após as grandes guerras, impulsionou a evolução dos sistemas criptográficos. O presente estudo aborda dois sistemas: a criptografia simétrica e a criptografia assimétrica, com ênfase no método RSA.
2. O que é Criptografia RSA?
RSA (Rivest-Shamir-Adleman) é um algoritmo de criptografia assimétrica desenvolvido em 1977. É reconhecido como um dos primeiros e mais amplamente utilizados sistemas de chave pública.
Características Principais
• Assimétrico: Utiliza duas chaves diferentes: uma chave pública e uma chave privada.
• Baseado em Problema Matemático: Sua segurança reside na dificuldade computacional de fatorar números grandes (o Problema da Fatoração).
• Bidirecional: Pode ser usado tanto para criptografar mensagens quanto para realizar assinatura digital.
• Amplamente Adotado: Serve como base para muitos protocolos de segurança utilizados atualmente (como HTTPS e SSH).
Princípio Básico
O fluxo básico envolve duas partes, Alice (dona da chave) e Bob (quem envia a mensagem):
1. Bob utiliza a chave pública de Alice para criptografar a mensagem.
2. Apenas Alice pode descriptografar a mensagem, utilizando sua chave privada secreta.
3. Fundamentos Matemáticos do RSA
A segurança e o funcionamento do RSA dependem de conceitos fundamentais da Teoria dos Números:
A. Aritmética Modular
A aritmética modular é essencial para o RSA. A notação a≡b(modn) significa que amodn=bmodn. Uma de suas propriedades importantes é a capacidade de calcular a exponenciação modular (a 
k
 modn) de forma eficiente, um processo fundamental para as operações de criptografia e descriptografia.
B. Números Primos
A importância dos números primos reside no Teorema Fundamental da Aritmética, que afirma que todo número possui uma fatoração prima única. O RSA utiliza dois primos grandes, p e q, para gerar o módulo n=p×q. O desafio de, dado n, encontrar p e q (o Problema da Fatoração) é o que garante a dificuldade de quebrar o sistema.
C. Função Totiente de Euler (φ(n))
Esta função conta quantos números menores que n são coprimos com n. Para o RSA, que usa o produto de dois primos distintos (n=p×q), a função é calculada de forma simples e secreta: 
φ(n)=(p−1)×(q−1)
.
D. Teorema de Euler e Inverso Modular
O Teorema de Euler é o que prova que o RSA funciona. Ele garante que, se a e n são coprimos, então a 
φ(n)
 ≡1(modn).
O conceito de Inverso Modular é usado para calcular a chave privada d. O valor d é o inverso modular do expoente público e módulo φ(n), de forma que: 
e×d≡1(modφ(n))
. O cálculo de d é feito utilizando o Algoritmo Euclidiano Estendido.
4. O Algoritmo RSA Passo-a-Passo
O processo do RSA é dividido em duas fases principais: Geração de Chaves e Operações.
Fase 1: Geração de Chaves
1. Gere Primos (p e q): Escolha dois números primos distintos, p e q, de tamanho similar. Para chaves de n bits (ex: 512 bits), p e q devem ter aproximadamente n/2 bits cada (ex: 256 bits). O teste de primalidade, como o teste de Miller-Rabin, é usado para garantir que esses números sejam provavelmente primos.
2. Calcule o Módulo (n): Calcule n=p×q. Este valor (n) será parte da chave pública.
3. Calcule φ(n): Calcule φ(n)=(p−1)×(q−1). Este valor deve ser mantido em segredo.
4. Escolha o Expoente Público (e): Escolha um valor e tal que 1<e<φ(n) e que seja coprimo com φ(n). O valor mais comum, 65537 (2 
16
 +1), é frequentemente utilizado por ser primo e tornar a exponenciação eficiente.
5. Calcule o Expoente Privado (d): Calcule d, o inverso modular de e(modφ(n)).
Resultado:
• Chave Pública: (n,e) (compartilhável).
• Chave Privada: (n,d) (secreta).
Fase 2: Operações de Criptografia e Descriptografia
A mensagem m deve ser um número menor que n.
Operação
Fórmula
Chave Utilizada
Criptografia
c=m 
e
 modn
Chave Pública (n,e)
Descriptografia
m=c 
d
 modn
Chave Privada (n,d)
5. Considerações de Segurança e Uso Recomendado
Segurança e Tamanho de Chave
A segurança do RSA é diretamente proporcional ao tamanho do módulo n.
• Chaves de 1024 bits são consideradas quebradas.
• Chaves de 2048 bits são atualmente consideradas seguras.
• Chaves de 3072 bits são recomendadas para uso a longo prazo.
Performance e Limitações
O RSA é computacionalmente caro.
• É aproximadamente 1000 vezes mais lento que algoritmos de criptografia simétrica, como o AES.
• Uso Típico: Devido à baixa performance, o RSA não é usado para criptografar grandes quantidades de dados. É idealmente usado para troca de chaves simétricas e assinatura digital.
Ataques Futuros
O RSA é vulnerável a ataques quânticos. O Algoritmo de Shor (1994) é capaz de quebrar o RSA em tempo polinomial se um computador quântico suficientemente grande for implementado, o que é estimado para ocorrer dentro de 10 a 20 anos. A contramedida será migrar para criptografia pós-quântica.
