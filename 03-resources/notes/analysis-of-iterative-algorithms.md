---
mocs:
    - "[[public-notes/03-resources/algorithms.moc.md|Algorithms & Data Structures]]"
tags:
    - cs/algorithms
---

+ **RAM model** (A computational model), RAM model assumes that each instruction takes the same amount of time as any other instruction and that each data access
+ **RAM** allows us to determine the best-case, worst-case and average-case time complexity of algorithms. recommendation is use wort-case cause it sets a boundary for any input
+ **Running times**: The running time of the algorithm is the sum of running times for each statement executed
+ We usually denote the running time of an algorithm on an input of size n by T(n)
+ we sum the products of the cost and times columns, obtaining
## Examples
### 1- Ex. insertion sort analysis
![[Pasted image 20240627223447.png]]
+ $\sum_{j=1}^{n-1}t_{j}$ depends of the input, ir represent the amount of times which the 5 line executes depending of each $j=1,2,3,4,5...$: $t_1$ represents the amount of times the 5 line is executed when $j=1$ and so on
### 2- Ex. nested loop dependent indexes
```Python
def algo(n):
	s=0 # c1,1
	i=1 # c2,1
	while i<=n: # c3,n+1
		t=0 # c4,n
		j=1 # c5,n
		while j<=i: # c6,n(n+3)/2
			t +=1  # c7,n(n+1)/2
			j +=1  # # c8,n(n+1)/2
		s+=t # c9,n
		i+=1 # c10,n
```

En el código anterior como i depende de j vamos a escribir la linea temporalmente como $\sum_{i=1}^{n}t_{i}$ (linea 6) ahora debemos analizar como se comporta $i$ vs $j$ para distintos valores de $n$ 

![[Pasted image 20240629102026.png]]

Como vemos en $i$ vs $j$ la formula que obtenemos sería $t_j=i+1$ por lo que si reemplazamos en la sumatoria por lo tanto si reemplazamos $t_j$ en la sumatoria que teníamos tenemos que: $\sum_{i=1}^{n}(i+1)$ solo queda transformar esta sumatoria a su forma cerrada  $\sum_{i=1}^{n}(i+1) =  n(n+3)/2$ y sumarlo con los termos de los costos de las otras lineas para obtener el polinomio total $T(n)$

```Python
def ex1_algo3_comp(n):
    l1 = 1
    l2 = 1
    l3 = n + 1
    l4 = n
    l5 = n
    l6 = n * (n + 3) // 2
    l7 = n * (n + 1) // 2
    l8 = n * (n + 1) // 2
    l9 = n
    l10 = n
    return l1 + l2 + l3 + l4 + l5 + l6 + l7 + l8 + l9 + l10
```
