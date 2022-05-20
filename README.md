# RL simples

Cov, Coefic de correlação e Coefic de determinação: cálculos que podem dizer a relação matemática entre 2 variáveis.
Cov: somatórios dos desvios de x . desvios de y /n-1
COef determinação  = cov(x,y)/sdx*sdy
#calculo passo a passo (sem funcaoes de cálculo)

tamanho_casas <- c(30,39,49,60)
preco_casas <- c(57.000,69.000,77.000,90.000)

frame_casas <- data.frame(tamanho_casas, preco_casas)
frame_casas$mediax <- mean(frame_casas[,1])
frame_casas$mediay <- mean(frame_casas[,2])
frame_casas$desx <- frame_casas$tamanho_casas - frame_casas$mediax
frame_casas$desy <- frame_casas$preco_casas - frame_casas$mediay
frame_casas$multdesv <- frame_casas$desx * frame_casas$desy
frame_casas$cov <- sum(frame_casas$multsdxy)/3
frame_casas$sdx <- sd(frame_casas$tamanho_casas)
frame_casas$multsdxy <- frame_casas$sdx * frame_casas$sdy
frame_casas$correlacao <- frame_casas$cov / frame_casas$multsdxy
frame_casas$coef_deter <- frame_casas$correlacao ^2
frame_casas

Cov: apenas consegue dizer se há interação, e em que direção, entre variáveis, mas, por estar em escalas diferentes, não permite inferir o gau de interação,
>0 interação posisitvs
<0 interação negativa
=0: sem interação

correlação: como resulado do cálculo (cov/sd) você tem a vo das varia´veis na mesma medida, podendo comparar a variabilidade de uma a outra, agora, podendo estabelecer o grau de intervação (para o grau, consultar tabela) r = var(xy)/sdx.sdy

Coef de determinação: como resultado do cálculo (cor^2) você terá a explicabilidade de uma variável sobre a outra, ou seja, o quanto a variável x, consegue explicar a variabilidade da variável y. este resultado é o mesmo que se obtem como resultado de uma RL simples.

##### 
Regressão linear é um algoritmo para calcular previsões, baseada na relação matemática entre 2 variáveis.
y = b0 + b1*x + e
Y = variável alvo (ou predita)
b0 = constante ou intercepto
b1 =coeficiente de angulação
x = variável explicativa ou preditora
e = ressíduo

Para encontrar o melhor ponto da reta, o algoritmo irá utilizar o MMQ (método de mínimos quadrados):
explicando: valor real - valor previsto = (erro)^2 - elevando ao quadrado ele poderá identificar melhor os erros maiores, além de descartar números ímpares, oq eu difiultaria o trabalho.
Após calcular o erro, ele somarará os resultados. O trabalho do algoritmo é treinar, e calcular todas as combinações possíveis, escolhendo a reta que tenha como resultado o menor valor no "e", que será, o ponto da reta que melhor vai prever o valor de y. para isso ele utilizar o método de descida do gradiente.
Como resultado, entregará o valor dos coeficientes utilizados (b0 e b1)
A linearidade, não vem da equação da reta, mas do método de cálculo do resíduo.
A correlação não mede a proporção em que y vai variar em relação a X, mas apenas o grau de associação linear (a correlação fere-se exclusivamente ao grau
de assiciação linear entre variáveis). Portanto, ela não dirá que, quando x variar, é muito provavel que haja variações positivas ou negativas em y, mas não
diráo quanto. Assm, mede-se numa escala de -1 a +1, quanto mais próximo do extremos, mais forte será associação entre elas.
Importante ressaltar que, uma correlação nula não implica necessariamente em ausência de associação entre variáveis, mas apenas que esta associação, se houve,
não é linear.

    ### RL SIMPLES
    
  Emobra a correlação seja uma medida útil para descobrir a assoaiação linear entre as variáveis, ela tem limitações, por exemplo: - quano y varia em relação
  a x, - dado um valor de x, qual valor poderei esperar de y? para estas respostas, você deve utilizar a regressão linear.
    A regressão linear representa a esperança condicional de y em função de x f(y|x), e pode-se representar da seguinte forma:
      E(y|x) = a + bxi = E(y) = a + bxi.
  E, uma vez que o modelo visa fazer previsões de yi (ou seja, valor de y, dado valor de x), espera-se que e=0 (espera-se que o modelo não erre em função do
  valor de x) a função do erro é representada por ei = yi - (a+bxi).
  
    OBSERVAÇÃO MINHA: quando o livro afirma que a esperença condicional do erri E(e1) = 0, e que a função do erro pode ser dada por e = yi - (a+bxi), parece
    redundante, pois y1 será sempre dados por E(yi) = a+bxi. Assim parece que ele será subtraido por ele mesmo, e o resultado sempre será 0.
  
  
  O intercept (a) representa o valor esperado de y quando x foi nulo, e o b1, representa a variação marginal de y da uma variação UNITÁRIA de x.
      Uma distinção importante entre a correlação e a regressão é que, nesta, supões que tanto o erro, quanto a variável y tenham natureza estocástica; já a variável indepedente, tem valor fixo, controlado pelo pesquisador. Assim sempre a afirmação será..dado x, qual seria o valor de y.
      A regresão deve fazer sentido e seguir a ordem lógica em coisas ocorre, ex: não seria lógico, num exemplo de produção agricola, tentar determinar
      quanto fertilizante irei usar, usando com variavel indenpendente a produção final obtida; na verdade, seria o inverso: dado valor x de fertilizante,
      quanto produzirei?
      
      #MMQ Ordinários
       Seja um con junto de informaçãoes (yi) dado como resultado de uma função matematia (f(0)), o MMQO utilizada uma série de princípios matemáticos que,
       ao realizar o cálculos do erro de previsão (e = yi-y), o elevará o quadrado, após realizando o somatório. A forma que apresentar o menor erro, será
       a que melhor descreve a relação quantitativa entre as variáveis x e y, resultando no modelo ajustado.
       O EQT (erro quadratico total) pode ser dado por: EQT = somatório e^2 ou somatório de [yi - f(0)]^2.
       Neste cálculo yi está representando o valor observado, e f(o) está rerpresentando a função de regressão
       
       
  


