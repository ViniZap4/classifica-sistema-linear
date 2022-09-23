# classifica-sistema-linear
> Atividade da diciplina método numéricos computaciona

# `LinearSystemClassify`
ver no [Notebook](./LinearSystemClassify.ipynb)

Para a criação da funcão eu usei: 
- O `numpy` para trabalhar com as matrizes
- E o `det` do `numpy.linalg` para os calculos

E fiz a stilização com o `colored` de `termcolor` 

## Criando a função `LinearSystemClassify`
```
def LinearSystemClassify(vecValue):
  
  #setting variables
  vecValue = np.array(vecValue) # full matrix vector values
  lenVecValue = len(vecValue)  # size of full vetor
  
  # matrix of coefficient
  matrixCoef = np.delete(vecValue, lenVecValue-1, 0)

  # independent term array
  independentTerm = vecValue[lenVecValue-1] 
  
  # Creating a matrixCoefx
  
  # adding size shape reference
  matrixCoefx = np.array([independentTerm]) 
  
  # adding respective column and line
  for i in range(lenVecValue-1):
     line = list()

     for j in range(len(vecValue[i])):
       #create line values

       if(j == 0): 
        line.append(independentTerm[i]) # adding independent term how firs column in line
       else:
         line.append(matrixCoef[i][j]) # adding rest values
            
       if(j == len(vecValue[i])-1):
         matrixCoefx = np.vstack([matrixCoefx,line]) #adding line to matrixCoefx  

  #delete shape reference line
  matrixCoefx = np.delete(matrixCoefx, 0, 0)


  
  title("\n----------LinearSytemClassify----------\n")
  subtitle("Matriz dos coeficientes:\n")
  print(matrixCoef)
  division("                        \n")
  subtitle("O termo independente é:\n")
  print(independentTerm)
  division("                         \n")
  subtitle("Matriz para a variavel x:\n")
  print(matrixCoefx)
  division("                         \n")
  
  #solve Linear system
  subtitle("Classificação:\n")
  detMatrixCoef = np.linalg.det(matrixCoef)
  detMatrixCoefx = np.linalg.det(matrixCoefx)

  if detMatrixCoef !=0: 
    solve = np.linalg.solve(matrixCoef,independentTerm)  # solving linear sytem if will be possible and determined
    print("SPD: Sistema Possivel Determinado,\n sendo sua solução:\n\n", solve)

  else:
    if detMatrixCoef ==0 and detMatrixCoefx ==0:
      print("SPI: Sistema Possivel e Indeterminado")
    else:
      print("SI: Sistema Impossivel")
  title("\n------------------//-------------------\n")
```

## Exemplo de uso

$$
\begin{cases}
2x-y=7   \\ 
x+5y=-2 
\end{cases}
$$

basta separar os coeficientes das equações e os termos independentes:

$$
  x \quad y \quad \quad \quad \quad z \\
\begin{matrix}
1. [2 & -1]  \\
2. [1 & 5]   \\
\end{matrix}
\quad 3.\begin{bmatrix}
7   \\
-2   \\
\end{bmatrix}
$$

e colocar no como parametro em um formato de array.

>**Lembrando que os termos termos independentes sempre serão adicionados por ultimo.**

```
# LinearSystemClassify([coeficientes da equação 1, coeficientes da equação 2, termos independentes(3)])

LinearSystemClassify([[2,-1],[1,5],[7,-5]])

```