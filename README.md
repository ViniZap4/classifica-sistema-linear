# classifica-sistema-linear
> Atividade da diciplina método numéricos computaciona

Para a resolução dessa atividade criei uma função para a classificação de sistemas lineares, sendo ela chamada de `LinearSystemClassify`:

- **SPD** (*Sistema Possível Determinado*)
- **SPI** (*Sistema Possível e Indeterminado*)
- **SI** (*Sistema Impossível*)

E recebe como parametro um array, contendo os valores dos coeficientes e dos termos indenpedentes e a própria função separa os termos e gera as matrizes respectivas para a classificação. caso o sistema linear for **SPD**, ele irá mostrar a solução do mesmo.

ver mais sobre o [LinearSystemClassify](./Notebooks/LinearSystemClassify.ipynb)