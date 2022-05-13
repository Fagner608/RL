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

correlação: como resulado do cálculo (cov/sd) você tem a vo das varia´veis na mesma medida, podendo comparar a variabilidade de uma a outra, agora, podendo estabelecer
o grau de intervação (para o grau, consultar tabela)

Coef de determinação: como resultado do cálculo (cor^2) você terá a explicabilidade de uma variável sobre a outra, ou seja, o quanto a variável x, consegue explicar a variabilidade da variável y. este resultado é o mesmo que se obtem como resultado de uma RL simples.

