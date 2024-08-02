---
title: "Interactuar con listas anidadas"
date: 2024-08-02
---

### Interactuar con listas anidadas

## Caso de Uso: Gestión de Productos en un Almacén

En este caso, tenemos una lista de productos en un almacén. Cada producto está representado por una lista que contiene un código, nombre, precio y stock. Necesitamos realizar varias operaciones comunes en la gestión de estos productos:

1. **Agregar un nuevo producto a la lista.**
2. **Actualizar la información de un producto existente.**
3. **Eliminar un producto de la lista.**
4. **Crear nuevas listas basadas en ciertas condiciones.**
5. **Generar informes de productos con ciertas características.**

### Lista Inicial de Productos

Esta es la lista inicial de productos:

```python
listas_de_productos = [
    ['A01', 'BOLSA CLAVOS 4 PULG.', 3500, 40],
    ['A02', 'TAPAGOTERAS SIKA', 6500, 60],
    ['A03', 'GUANTES DE CUERO', 3000, 35],
    ['A04', 'BOTELLA DILUYENTE', 1200, 70],
    ['A05', 'AMPOLLETA 60 W.', 2400, 80],
    ['A06', 'ESMERIL ANGULAR', 18000, 25],
    ['A07', 'TALADRO PERCUTOR', 25000, 45],
    ['A08', 'ALICATE', 3800, 55],
    ['A09', 'MARTILLO', 5600, 36],
    ['A10', 'ESMALTE AL AGUA BLANCO', 8500, 98]
]
```

### 1. Agregar un Nuevo Producto

**Problema:**
Necesitamos agregar un nuevo producto a la lista `listas_de_productos`. Esto es común cuando se reciben nuevos productos en el almacén.

**Solución:**
Usaremos el método `append()` para agregar un nuevo producto.

```python
# Solicitar datos del nuevo producto al usuario
codigo = input("Ingrese el código del nuevo producto: ")
nombre = input("Ingrese el nombre del nuevo producto: ")
precio = int(input("Ingrese el precio del nuevo producto: "))
stock = int(input("Ingrese el stock del nuevo producto: "))

# Nuevo producto
nuevo_producto = [codigo, nombre, precio, stock]

# Agregar el nuevo producto a la lista
listas_de_productos.append(nuevo_producto)

# Imprimir la lista actualizada
print("Lista de productos actualizada:")
for producto in listas_de_productos:
    print(producto)
```

**Explicación:**
El método `append()` añade el nuevo producto al final de la lista `listas_de_productos`.

### 2. Actualizar un Producto Existente

**Problema:**
El precio y el stock de un producto han cambiado. Necesitamos actualizar estos valores en nuestra lista.

**Solución:**
Recorreremos la lista para encontrar el producto y actualizar su precio y stock.

```python
# Solicitar el código del producto a actualizar
codigo = input("Ingrese el código del producto a actualizar: ")

# Recorrer la lista para encontrar el producto con el código ingresado
for producto in listas_de_productos:
    if producto[0] == codigo:  # Código del producto
        nuevo_precio = int(input("Ingrese el nuevo precio del producto: "))
        nuevo_stock = int(input("Ingrese el nuevo stock del producto: "))
        producto[2] = nuevo_precio   # Nuevo precio
        producto[3] = nuevo_stock    # Nuevo stock
        break
else:
    print("Producto no encontrado")

# Imprimir la lista actualizada
print("Lista de productos actualizada:")
for producto in listas_de_productos:
    print(producto)
```

**Explicación:**
Usamos un ciclo `for` para encontrar el producto con el código ingresado por el usuario y actualizamos sus valores de precio y stock directamente.

### 3. Eliminar un Producto

**Problema:**
Un producto ya no está disponible y necesitamos eliminarlo de nuestra lista.

**Solución:**
Recorreremos la lista para encontrar el producto y eliminarlo usando el método `remove()`.

```python
# Solicitar el código del producto a eliminar
codigo = input("Ingrese el código del producto a eliminar: ")

# Recorrer la lista para encontrar el producto a eliminar
for producto in listas_de_productos:
    if producto[0] == codigo:  # Código del producto
        listas_de_productos.remove(producto)
        break
else:
    print("Producto no encontrado")

# Imprimir la lista actualizada
print("Lista de productos actualizada:")
for producto in listas_de_productos:
    print(producto)
```

**Explicación:**
Usamos un ciclo `for` para encontrar el producto con el código ingresado por el usuario y lo eliminamos usando `remove()`. El `break` se usa para salir del ciclo después de eliminar el producto.

### 4. Crear Nuevas Listas Basadas en Condiciones

**Problema:**
Queremos crear listas que contengan productos específicos según ciertas condiciones.

**Solución 1:**
Crear una lista con los nombres de los productos que tienen un stock mayor a 50.

```python
# Crear una nueva lista con nombres de productos con stock mayor a 50
productos_stock_alto = []

# Recorrer la lista original y agregar nombres a la nueva lista
for producto in listas_de_productos:
    if producto[3] > 50:  # Verificar si el stock es mayor a 50
        productos_stock_alto.append(producto[1])  # Agregar el nombre del producto a la nueva lista

# Imprimir la nueva lista
print("Productos con stock mayor a 50:")
for nombre in productos_stock_alto:
    print(nombre)
```

**Solución 2:**
Crear una lista con productos cuyo precio es menor a 4000.

```python
# Crear una nueva lista con productos cuyo precio es menor a 4000
productos_precio_bajo = []

# Recorrer la lista original y agregar productos a la nueva lista
for producto in listas_de_productos:
    if producto[2] < 4000:  # Verificar si el precio es menor a 4000
        productos_precio_bajo.append(producto)

# Imprimir la nueva lista
print("Productos con precio menor a 4000:")
for producto in productos_precio_bajo:
    print(producto)
```

**Solución 3:**
Crear una lista con productos cuyo nombre contiene la palabra "ALICATE".

```python
# Crear una nueva lista con productos cuyo nombre contiene "ALICATE"
productos_con_alicate = []

# Recorrer la lista original y agregar productos a la nueva lista
for producto in listas_de_productos:
    if 'ALICATE' in producto[1]:  # Verificar si el nombre contiene "ALICATE"
        productos_con_alicate.append(producto)

# Imprimir la nueva lista
print("Productos que contienen 'ALICATE' en su nombre:")
for producto in productos_con_alicate:
    print(producto)
```

**Explicación:**
Usamos ciclos `for` y condiciones `if` para crear nuevas listas basadas en condiciones específicas.

### 5. Generar Informes de Productos

**Problema:**
Queremos generar informes de productos con ciertas características para facilitar el análisis.

**Solución 1:**
Generar un informe simple con los nombres y precios de todos los productos.

```python
# Recorrer la lista original y imprimir nombre y precio de cada producto
print("Informe de todos los productos:")
for producto in listas_de_productos:
    print(f'Producto: {producto[1]}, Precio: {producto[2]}')
```

**Solución 2:**
Generar un informe de productos con precio mayor a 5000.

```python
# Recorrer la lista original y imprimir nombre y precio de cada producto con precio > 5000
print("Informe de productos con precio mayor a 5000:")
for producto in listas_de_productos:
    if producto[2] > 5000:  # Verificar si el precio es mayor a 5000
        print(f'Producto: {producto[1]}, Precio: {producto[2]}')
```

**Solución 3:**
Generar un informe de productos con stock entre 30 y 60 unidades.

```python
# Recorrer la lista original y imprimir nombre y stock de cada producto con stock entre 30 y 60
print("Informe de productos con stock entre 30 y 60:")
for producto in listas_de_productos:
    if 30 <= producto[3] <= 60:  # Verificar si el stock está entre 30 y 60
        print(f'Producto: {producto[1]}, Stock: {producto[3]}')
```

**Explicación:**
Usamos ciclos `for` y condiciones `if` para generar informes basados en características específicas.

---

### Resumen de Todas las Operaciones en Código

```python
listas_de_productos = [
    ['A01', 'BOLSA CLAVOS 4 PULG.', 3500, 40],
    ['A02', 'TAPAGOTERAS SIKA', 6500, 60],
    ['A03', 'GUANTES DE CUERO', 3000, 35],
    ['A04', 'BOTELLA DILUYENTE', 1200, 70],
    ['A05', 'AMPOLLETA

 60 W.', 2400, 80],
    ['A06', 'ESMERIL ANGULAR', 18000, 25],
    ['A07', 'TALADRO PERCUTOR', 25000, 45],
    ['A08', 'ALICATE', 3800, 55],
    ['A09', 'MARTILLO', 5600, 36],
    ['A10', 'ESMALTE AL AGUA BLANCO', 8500, 98]
]

# 1. Agregar un nuevo producto
codigo = input("Ingrese el código del nuevo producto: ")
nombre = input("Ingrese el nombre del nuevo producto: ")
precio = int(input("Ingrese el precio del nuevo producto: "))
stock = int(input("Ingrese el stock del nuevo producto: "))
nuevo_producto = [codigo, nombre, precio, stock]
listas_de_productos.append(nuevo_producto)
print("Lista de productos actualizada:")
for producto in listas_de_productos:
    print(producto)

# 2. Actualizar un producto existente
codigo = input("Ingrese el código del producto a actualizar: ")
for producto in listas_de_productos:
    if producto[0] == codigo:
        nuevo_precio = int(input("Ingrese el nuevo precio del producto: "))
        nuevo_stock = int(input("Ingrese el nuevo stock del producto: "))
        producto[2] = nuevo_precio
        producto[3] = nuevo_stock
        break
else:
    print("Producto no encontrado")
print("Lista de productos actualizada:")
for producto in listas_de_productos:
    print(producto)

# 3. Eliminar un producto
codigo = input("Ingrese el código del producto a eliminar: ")
for producto in listas_de_productos:
    if producto[0] == codigo:
        listas_de_productos.remove(producto)
        break
else:
    print("Producto no encontrado")
print("Lista de productos actualizada:")
for producto in listas_de_productos:
    print(producto)

# 4. Crear nuevas listas basadas en condiciones
productos_stock_alto = []
for producto in listas_de_productos:
    if producto[3] > 50:
        productos_stock_alto.append(producto[1])
print("Productos con stock mayor a 50:")
for nombre in productos_stock_alto:
    print(nombre)

productos_precio_bajo = []
for producto in listas_de_productos:
    if producto[2] < 4000:
        productos_precio_bajo.append(producto)
print("Productos con precio menor a 4000:")
for producto in productos_precio_bajo:
    print(producto)

productos_con_alicate = []
for producto in listas_de_productos:
    if 'ALICATE' in producto[1]:
        productos_con_alicate.append(producto)
print("Productos que contienen 'ALICATE' en su nombre:")
for producto in productos_con_alicate:
    print(producto)

# 5. Generar informes de productos
print("Informe de todos los productos:")
for producto in listas_de_productos:
    print(f'Producto: {producto[1]}, Precio: {producto[2]}')

print("Informe de productos con precio mayor a 5000:")
for producto in listas_de_productos:
    if producto[2] > 5000:
        print(f'Producto: {producto[1]}, Precio: {producto[2]}')

print("Informe de productos con stock entre 30 y 60:")
for producto in listas_de_productos:
    if 30 <= producto[3] <= 60:
        print(f'Producto: {producto[1]}, Stock: {producto[3]}')
```
