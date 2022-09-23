# classifica-sistema-linear
 Atividade da diciplina método numéricos computaciona
 


```
from IPython.core.magics.pylab import line_magic
def LinearSytemClassify(vecValue):
  
  #setting variables
  vecValue = np.array(vecValue)
  lenVecValue = len(vecValue) 
 
  matrizCoef = np.delete(vecValue, lenVecValue-1, 0)


  independentTerm = vecValue[lenVecValue-1]
  
  matrizCoefx = np.array([independentTerm]) # adding size shape
  

  for i in range(lenVecValue-1):
     line = list()

     for j in range(len(vecValue[i])):
       #create column values

       if(j == 0):
        line.append(independentTerm[i]) # adding indempendent term how first column
       else:
         line.append(matrizCoef[i][j]) # adding rest
            
       if(j == len(vecValue[i])-1):
         matrizCoefx = np.vstack([matrizCoefx,line]) #adding line to matrizCoefx  

  #delete shape item
  matrizCoefx = np.delete(matrizCoefx, 0, 0)



  print("\n#####################################\n")
  print("Matriz dos coeficientes:\n", matrizCoef)
  print("\n--------------\n")
  print("O termo independen é:\n", independentTerm)
  print("\n--------------\n")
  print("Matriz para a variavel x:\n", matrizCoefx)

  #solve Linear system
  print("\n--------------\n")
  print("Solução:")
  detMatrizCoef = np.linalg.det(matrizCoef)
  detMatrizCoefx = np.linalg.det(matrizCoefx)

  if detMatrizCoef !=0:
    solve = np.linalg.solve(detMatrizCoef,independentTerm)
    print("Sistema Possivel Determinado, sendo sua solução:\n", solve)

  else:
    if detMatrizCoef ==0 and detMatrizCoefx ==0:
      print("Sistema Possivel e Indeterminado")
    else:
      print("Sistema Impossivel")
  print("\n#####################################")

LinearSytemClassify([[2,3],[4,6],[1,2]])
```
