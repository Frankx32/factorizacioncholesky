# 
de  choldate  import  cholupdate , choldowndate 
import  numpy

#Cree una matriz definida positiva aleatoria, V 
numpy . al azar . semilla ( 1 )
 X  =  numpy . al azar . normal ( tamaño = ( 100 , 10 ))
 V  =  numpy . punto ( X . transpuesta (), X )

#Calcule el factor Cholesky superior, R 
R  =  numpy . linalg . cholesky ( V ). transponer ()

# Cree un vector de actualización aleatorio, u 
u  =  numpy . al azar . normales ( tamaño = R . forma [ 0 ])

# Calcule la matriz definida positiva actualizada, V1, y su factor de Cholesky, R1 
V1  =  V  +  numpy . exterior ( u , u )
 R1  =  numpy . linalg . cholesky ( V1 ). transponer ()

# El siguiente es equivalente a la anterior 
R1_  =  R . copiar ()
 cholupdate ( R1_ , u . copiar ())
 afirmar ( numpy . todo (( R1  -  R1_ ) ** 2  <  1e-16 ))

#Y la desactualización es lo contrario de actualizar 
R_  =  R1 . copiar ()
 choldowndate ( R_ , u . copiar ())
 afirmar ( numpy . todo (( R  -  R_ ) ** 2  <  1e-16 ))  
