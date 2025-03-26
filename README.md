# Explicação N1 Ney

Versão 1: Algoritmo Básico
Saída
Sequência de entregas: [(0, 'B', 1), (10, 'D', 8)]
Lucro total: 9
Tempo de execução: 0.0001s
Explicação do Resultado
O algoritmo básico processa as entregas na ordem em que aparecem, verificando se é possível realizá-las com base no tempo disponível. Vamos analisar passo a passo:
Dados de Entrada:
Conexões:
A → B: 5 minutos
B → C: 3 minutos
A → D: 2 minutos
C → D: 8 minutos
Entregas:
(0, B, 1): Entrega para B, início no minuto 0, bônus 1.
(5, C, 10): Entrega para C, início no minuto 5, bônus 10.
(10, D, 8): Entrega para D, início no minuto 10, bônus 8.
Processamento:
Entrega para B (início 0):
Tempo de A → B: 5 minutos (ida).
Tempo total (ida e volta): 5 + 5 = 10 minutos.
O entregador sai de A no minuto 0, chega em B no minuto 5, e retorna a A no minuto 10.
Bônus: 1.
Tempo atual após a entrega: 10 minutos.
Entrega para C (início 5):
O entregador só retorna a A no minuto 10, mas a entrega para C deveria começar no minuto 5. Como o entregador não está em A no minuto 5, essa entrega é perdida.
Entrega para D (início 10):
O entregador está de volta a A no minuto 10, exatamente quando a entrega para D deve começar.
Tempo de A → D: 2 minutos (ida).
Tempo total (ida e volta): 2 + 2 = 4 minutos.
O entregador sai de A no minuto 10, chega em D no minuto 12, e retorna a A no minuto 14.
Bônus: 8.
Tempo atual após a entrega: 14 minutos.
Resultado Final:
Sequência: [(0, 'B', 1), (10, 'D', 8)] – O algoritmo escolheu as entregas para B e D.
Lucro total: 1 (B) + 8 (D) = 9.
Tempo de execução: 0.0001s, indicando que o algoritmo é muito rápido, pois é linear (processa as entregas uma a uma).
Gráficos
Simulação de Entregas – Versão 1 (Lucro Total: 9):
Eixo X (Destinos): Mostra os destinos B e D.
Eixo Y (Bônus): Mostra os bônus de cada entrega (1 para B, 8 para D).
Anotações: Acima de cada barra, o tempo de início é indicado (T=0 para B, T=10 para D).
Interpretação: O gráfico visualiza as entregas realizadas, destacando que B foi feita primeiro (com um bônus pequeno) e D foi feita depois (com um bônus maior), totalizando 9 de lucro.
Lucro Obtido – Versão 1:
Eixo X: Mostra "Versão 1".
Eixo Y (Lucro): Mostra o lucro total de 9.
Interpretação: Este gráfico de barras simples confirma o lucro total obtido pela Versão 1.
Resumo
A Versão 1 prioriza a ordem das entregas e não otimiza o lucro. Como a entrega para B foi feita primeiro, o entregador perdeu a entrega para C (que tinha um bônus maior, 10), mas conseguiu fazer a entrega para D. O lucro total foi 9, que não é o máximo possível.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Versão 2: Algoritmo com IA (continuação)
Explicação do Resultado
O algoritmo com IA utiliza busca exaustiva (testando todas as permutações possíveis das entregas) para encontrar a combinação que maximiza o lucro, respeitando as restrições de tempo. Vamos analisar o processo passo a passo:
Dados de Entrada:
Conexões:
A → B: 5 minutos
B → C: 3 minutos
A → D: 2 minutos
C → D: 8 minutos
Entregas:
(0, B, 1): Entrega para B, início no minuto 0, bônus 1.
(5, C, 10): Entrega para C, início no minuto 5, bônus 10.
(10, D, 8): Entrega para D, início no minuto 10, bônus 8.
Processamento: O algoritmo testa todas as permutações possíveis das entregas (B, C, D) para encontrar a sequência que maximiza o lucro. Há 3! = 6 permutações possíveis: (B, C, D), (B, D, C), (C, B, D), (C, D, B), (D, B, C), (D, C, B). Vamos analisar algumas combinações principais:
Permutação 1: (B, C, D) (começando com B):
Entrega para B (início 0):
Tempo de A → B: 5 minutos (ida).
Tempo total (ida e volta): 5 + 5 = 10 minutos.
O entregador sai de A no minuto 0, chega em B no minuto 5, e retorna a A no minuto 10.
Bônus: 1.
Tempo atual: 10 minutos.
Entrega para C (início 5):
O entregador só retorna a A no minuto 10, mas a entrega para C deveria começar no minuto 5. Como o entregador não está em A no minuto 5, essa entrega é perdida.
Entrega para D (início 10):
O entregador está de volta a A no minuto 10, então pode fazer a entrega para D.
Tempo de A → D: 2 minutos (ida).
Tempo total (ida e volta): 2 + 2 = 4 minutos.
O entregador sai de A no minuto 10, chega em D no minuto 12, e retorna a A no minuto 14.
Bônus: 8.
Tempo atual: 14 minutos.
Lucro dessa sequência: 1 (B) + 8 (D) = 9.
Permutação 2: (C, B, D) (começando com C):
Entrega para C (início 5):
Tempo de A → C: A → B (5 minutos) + B → C (3 minutos) = 8 minutos (ida).
Tempo total (ida e volta): 8 + 8 = 16 minutos.
O entregador sai de A no minuto 5, chega em C no minuto 13, e retorna a A no minuto 21.
Bônus: 10.
Tempo atual: 21 minutos.
Entrega para B (início 0):
O entregador só retorna a A no minuto 21, mas a entrega para B deveria começar no minuto 0. Essa entrega já foi perdida.
Entrega para D (início 10):
O entregador retorna a A no minuto 21, mas a entrega para D deveria começar no minuto 10. Essa entrega também foi perdida.
Lucro dessa sequência: 10 (C) = 10.
Permutação 3: (D, B, C) (começando com D):
Entrega para D (início 10):
Tempo de A → D: 2 minutos (ida).
Tempo total (ida e volta): 2 + 2 = 4 minutos.
O entregador sai de A no minuto 10, chega em D no minuto 12, e retorna a A no minuto 14.
Bônus: 8.
Tempo atual: 14 minutos.
Entrega para B (início 0):
O entregador retorna a A no minuto 14, mas a entrega para B deveria começar no minuto 0. Essa entrega foi perdida.
Entrega para C (início 5):
O entregador retorna a A no minuto 14, mas a entrega para C deveria começar no minuto 5. Essa entrega também foi perdida.
Lucro dessa sequência: 8 (D) = 8.
Melhor sequência: [(5, 'C', 10)]
Lucro total: 10.
Por que apenas C foi escolhida?
A entrega para C tem o maior bônus (10), mas seu horário de início (minuto 5) impede que outras entregas sejam feitas antes ou depois:
Se fizer B primeiro (início 0), o entregador só retorna a A no minuto 10, perdendo C (início 5).
Se fizer C primeiro (início 5), o entregador retorna a A no minuto 21, perdendo B (início 0) e D (início 10).
Se fizer D primeiro (início 10), o entregador retorna a A no minuto 14, perdendo B (início 0) e C (início 5).
A melhor opção é fazer apenas a entrega para C, que dá um lucro de 10, maior do que qualquer outra combinação (como B e D, que dá 9).
Tempo de Execução:
0.0002s: O algoritmo é mais lento que a Versão 1 (0.0001s) porque testa todas as permutações (busca exaustiva), o que tem complexidade fatorial (O(n!)). Para 3 entregas, isso é rápido, mas para mais entregas, o tempo de execução aumentaria significativamente.
Gráficos
Simulação de Entregas – Versão 2 (Lucro Total: 10):
Eixo X (Destinos): Mostra apenas o destino C.
Eixo Y (Bônus): Mostra o bônus de 10 para C.
Anotações: Acima da barra, o tempo de início é indicado (T=5 para C).
Interpretação: O gráfico visualiza que apenas a entrega para C foi realizada, com um bônus de 10, resultando em um lucro total de 10. A escolha de C maximiza o lucro, mas impede outras entregas devido ao tempo.
Lucro Obtido – Versão 2:
Eixo X: Mostra "Versão 2".
Eixo Y (Lucro): Mostra o lucro total de 10.
Interpretação: Este gráfico de barras simples confirma o lucro total obtido pela Versão 2, que é maior que o da Versão 1 (9).
Resumo
A Versão 2 usa IA (busca exaustiva) para encontrar a solução ótima, maximizando o lucro. Ela escolheu apenas a entrega para C (bônus 10), pois fazer outras entregas (B ou D) resultaria em perder C, que tem o maior bônus. O lucro total foi 10, que é o máximo possível nesse cenário. No entanto, o algoritmo é mais lento que a Versão 1 devido à busca exaustiva.

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Comparação Geral entre Versão 1 e Versão 2
Lucro:
Versão 1: 9 (B e D).
Versão 2: 10 (C).
A Versão 2 obteve um lucro maior porque considera todas as combinações possíveis e escolhe a mais lucrativa, enquanto a Versão 1 processa as entregas na ordem e perde oportunidades (como a entrega para C).
Tempo de Execução:
Versão 1: 0.0001s (mais rápido, pois é linear).
Versão 2: 0.0002s (mais lento, pois é fatorial).
A Versão 1 é mais eficiente em termos de tempo, mas não otimiza o lucro. A Versão 2 é mais lenta, mas garante o melhor resultado.
Gráficos:
A simulação da Versão 1 mostra duas entregas (B e D), enquanto a da Versão 2 mostra apenas uma (C), refletindo a escolha otimizada.
Os gráficos de lucro mostram que a Versão 2 alcança um lucro maior (10 vs. 9).
Conclusão
Versão 1: É mais rápida e simples, mas não otimiza o lucro. Escolheu B e D (lucro 9), perdendo a entrega mais lucrativa (C).
Versão 2: É mais lenta, mas maximiza o lucro. Escolheu apenas C (lucro 10), que é a melhor opção possível nesse cenário.
Gráficos: Os gráficos ajudam a visualizar as entregas realizadas e o lucro obtido, destacando a diferença de desempenho entre as duas versões.
