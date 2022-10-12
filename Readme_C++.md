# Proyecto realizado en Python
**El siguiente proyecto esta basado en el manejo de archivos, en el cual consta de un menu con 3 opciones para la creacion del archivo, lectura del archivo, manipulacion del archuivo**

##DEclaracion de las variables 
`class producto:
    nombre = ""
    codigo = 0
    precio = 0
    proveedor = ""
    existencia = -0
    estado = ""<
    descuento = -0 
    `

### Declaracion del la opcion 1 del menu(Ingesar Productos)
**En el siguiente bloque de codigo se realiza la creacin de un nuevo producto, en el cual se ingresa el nombre, codigo, precio, proveedor, existencia, estado y descuentos del producto asi mismo se guarda en un archivo .CSV**
```python
with open("productos.csv","a") as archivo:
        p = producto()
        p.nombre = input("Ingrese nombre: ")
        p.codigo = input("Ingrese codigo: ")
        p.precio = input("Ingrese precio: ")
        p.proveedor = input("Ingrese proveedor: ")
        p.existencia = input("Ingrese existencia: ")
        p.estado = input("Ingrese estado: ")
        p.descuento = input("Ingrese descuento: ")

        archivo.write(p.nombre+ "," + p.codigo+ "," + p.precio+ "," + p.proveedor+ "," + p.existencia+ "," + p.estado+ "," + p.descuento+ "\n" )
        archivo.close() 
```
#### Declaracion de la opcion de modificar algun producto en especeifico
**En el siguiente codigo se pueder realizar la modificacion de un producto en especifico, lo realiza tomando el archivo .CSV y por medio del codigo del producto se le aplica un If y un For se genera un menu para seleccionar que campo del producto desea modificar**

**Menu de la varaible modificar**
```python

                    print("1) Producto:")
                    print("2) Precio:")
                    print("3) Proveedor:")
                    print("4) Existencia:")
                    print("5) Estado:")
                    print("6) Descuento:")
                    valor = input("Que propiedad desea modificar: ")
```
**codigo fuente de la variable modificar, al momento de modificar solicitara que campo desea modificar**
```python
if int(valor) in [1,2,3,4,5,7]:                    
                        
                        p = producto()
                        p.nombre = l[0]
                        p.codigo =l[1]
                        p.precio =l[2]
                        p.proveedor =l[3]
                        p.existencia=l[4]
                        p.estado=l[5]
                        p.descuento=l[6]
                        
                        if int(valor) == 1:
                            p.nombre=input("Nombre de producto: ")
                        if int(valor) == 2:
                            p.precio=input("Ingrese nuevo precio")
                        if int(valor) == 3:
                            p.proveedor=input("nuevo valor proveedor")
                        if int(valor) == 4:
                            p.existencia=input("nuevo valor existencia")
                        if int(valor) == 5:
                            p.estado=input("nuevo valor estado")
                        if int(valor) == 6:
                            p.descuento=input("nuevo valor descuento")
```
**Al momento de modificar el archivo se guardan los datos en el archivo: productos.csv**
```python
with open("productos.csv","a") as archivo:
                             archivo.write(p.nombre+ "," + p.codigo+ "," + p.precio+ "," + p.proveedor+ "," + p.existencia+ "," + p.estado+ "," + p.descuento+ "\n" )
                             archivo.close() 
```
**En dado caso el usuario ingres mal un codigo generara lo siguiente:**
`
                    ("propiedad no existe")
                    return
                    `

**Se cuenta con la opcion de buscar en el programa el cual lo va realizar por medio del codigo del producto**
```python
def buscar ():
    codigo = input("ingrese el codigo de producto: ")
    with open("productos.csv","r") as archivo:
        for p in archivo:
            l = p.split(sep=',')
            if codigo in l :
                print("Producto: "+l[0])
                print("Codigo: "+l[1])
                print("Precio: "+l[2])
                print("Proveedor: "+l[3])
                print("Existencia: "+l[4])
                print("Estado: "+l[5])
                print("Descuento: "+l[6])   
```
**En dado caso el usuario ingrese un numero que no este en el menu el programa realizara lo siguiente:**
```python
while  True:
   	try:
   		print("Menú")
   		print ("[1] Ingresar producto ")
   		print ("[2] modificar producto")
   		print ("[3] Buscar producto")
   		print ("[4] Salir")
    
   		ope = int(input("Que deseas realizar: "))
   	except ValueError:
   		print("Porfavor ingresa una opcion valida")
   	else:
   		
   		if ope < 1 or ope >4:
   				print ("no es una opcion valida")
   				continue
   		if ope == 1:
   			ingresar_producto()
   		elif ope == 2:
   			modificar()
   		elif ope == 3:
   			buscar()
   		else:
   			break
```

**Para finalizar el programa mostrara el siguiente mensaje:**
`print ("Gracias por utilizar esta aplicacion")`







    
