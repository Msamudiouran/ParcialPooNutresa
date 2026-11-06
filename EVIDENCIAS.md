# Evidencias: Miguel Ángel Samudio Urán

## 1. Errores de sintaxis corregidos
| # | Archivo | Línea | Mensaje del compilador | Corrección |
|---|---------|-------|------------------------|------------|
| 1 | Condimento.java | 9 | cannot find symbol alFinal | Se cambió `alFinal` por `seAgregaAlFinal` en el constructor. |
| 2 | Condimento.java | 17 | variable minutos might not have been initialized | Se inicializó `int minutos = 0;` en la declaración. |
| 3 | Costeable.java | 4 | interface abstract methods cannot have body | Se eliminó el cuerpo `{ return 0; }` y se dejó solo la firma con punto y coma. |
| 4 | Identificable.java | 4 | ';' expected | Se agregó el punto y coma faltante al final de `getCodigo()`. |
| 5 | Ingrediente.java | 26 | incompatible types: int cannot be converted to double | Se corrigió el tipo de retorno de `getPrecioKilo()` a `double`. |
| 6 | Ingrediente.java | 42 | cannot find symbol class IllegalArgumentException | Se agregó la palabra clave `new` antes de `IllegalArgumentException`. |
| 7 | Ingrediente.java | 72 | unclosed string literal | Se corrigió el salto de línea dentro de las comillas en `obtenerFicha()`. |
| 8 | Olla.java | 37 | illegal start of expression / syntax error | Se restauró la llave de cierre `}` del método `agregarIngrediente()`. |
| 9 | Olla.java | 41 | missing return statement | Se agregó `return null;` al final de `buscarPorCodigo()`. |
| 10 | Olla.java | 54 | cannot find symbol method length() | Se cambió `ingredientes.length` por `ingredientes.size()`. |
| 11 | Olla.java | 63 | operator < cannot be applied | Se corrigió la lógica del ciclo de tiempo de cocción para buscar el mayor. |
| 12 | Pedido.java | 33 | cannot find symbol variable getPrecio | Se agregaron los paréntesis faltantes `a.getPrecio()`. |
| 13 | Proteina.java | 7 | constructor Ingrediente cannot be applied | Se añadió el parámetro `fresco` faltante en la llamada a `super()`. |
| 14 | Proteina.java | 17 | incompatible types: String cannot be converted to int | Se cambió `"60"` por el número entero `60`. |
| 15 | Sancocho.java | 20 | syntax error on token '.', { expected | Se eliminó el punto sobrante `.` antes del `@Override`. |
| 16 | Sancocho.java | 34 | non-static method cannot be referenced from a static context | Se cambió `Olla.calcularTiempoCoccion()` por la instancia `olla.calcularTiempoCoccion()`. |
| 17 | Sancocho.java | 46 | incompatible types: unexpected return value | Se cambió el tipo de retorno de `void` a `boolean` en el método `servir()`. |
| 18 | Tuberculo.java | 6 | constructor Tuberculos in class Tuberculo cannot be applied | Se renombró el constructor de `Tuberculos` a `Tuberculo`. |
| 19 | Tuberculo.java | 22 | invalid character constant | Se cambiaron las comillas simples `'Tubérculo'` por dobles `"Tubérculo"`. |
| 20 | Verdura.java | 3 | syntax error on token 'extend', 'extends' expected | Se corrigió `extend` por `extends`. |
| 21 | Verdura.java | 11 | method does not override or implement a method from a supertype | Se renombró `minutosDeCoccion()` a `minutosCoccion()`. |
| 22 | Fonda.java | 3 | package java.util.ArrayList does not exist | Se agregó `import java.util.ArrayList;`. |
| 23 | Fonda.java | 63 | package system does not exist | Se corrigió `system.out.println` a `System.out.println`. |
| 24 | Fonda.java | 44 | constructor Pedido cannot be applied | Se incluyó el argumento `cantidad` en la instanciación de `Pedido`. |
| 25 | Main.java | 15 | Yuca is abstract; cannot be instantiated | Se cambió `new Ingrediente(...)` por `new Tuberculo(...)`. |

## 2. Errores de lógica corregidos
| # | Archivo y método | Qué hacía mal | Pista (fila de la tabla) | Cómo lo corregí |
|---|------------------|---------------|--------------------------|-----------------|
| 1 | Ingrediente.calcularCosto() | Divulgaba división entera truncada (`gramos / 1000`) | Sección 1 (Costos de la olla) | Se aseguró la división decimal antes de multiplicar por el precio kilo. |
| 2 | Olla.calcularCostoIngredientes() | Iniciaba el ciclo en `i = 1` omitiendo el primer ingrediente | Sección 1 (Costos de la olla) | Se cambió el índice inicial del bucle a `i = 0`. |
| 3 | Olla.calcularTiempoCoccion() | Buscaba el menor tiempo (`< mayor`) en lugar del mayor | Sección 1 (Minutos de la olla) | Se ajustó la condición para evaluar el ingrediente más demorado (`> mayor`). |
| 4 | Tuberculo.minutosCoccion() | Invertía los tiempos asignando 25 para duros y 40 para blandos | Sección 2 (Olla trifásica) | Se configuró el operador ternario para retornar 40 si es duro y 25 si no. |
| 5 | Sancocho.calcularCosto() | Multiplicaba mal el costo del gas | Sección 4 (Ficha del sancocho) | Se multiplicó el tiempo de cocción por la constante `COSTO_GAS_POR_MINUTO`. |
| 6 | Sancocho.estaCompleto() | Tenía una condición incorrecta con OR (`\|\|`) | Sección 4 (¿Está completo?) | Se ajustaron los operadores lógicos con AND (`&&`) para exigir los tres tipos. |
| 7 | Sancocho.esTrifasico() | Validaba la cantidad total de ingredientes en vez de contar proteínas | Sección 4 (¿Es trifásico?) | Se actualizó para contabilizar específicamente la categoría `"Proteina" >= 3`. |
| 8 | Pedido.calcularCosto() | Sumaba los acompañamientos al final sin multiplicarlos por la cantidad de platos | Sección 5 (Pedidos mesa 1 y 2) | Se encapsuló la suma del plato y acompañamientos multiplicada por `cantidad`. |
| 9 | Fonda.registrarPedido() | Agregaba el pedido a la lista antes de verificar si alcanzaban las porciones | Sección 5 (Mesas rechazadas) | Se validó primero la disponibilidad con `sancocho.servir(cantidad)` antes de registrarlo. |
| 10 | Main.java (Polimorfismo) | Realizaba una búsqueda de métodos con casting impreciso en la sección 6 | Sección 6 (Polimorfismo) | Se ajustó el casteo correcto a `(Proteina)` en el retorno de `buscarPorCodigo`. |

## 3. Salida final del programa
```text
=== 1. Olla del sancocho de gallina ===
¿Se aceptó un ingrediente que no está fresco? false
¿Se aceptó un código repetido? false
Olla (4470/6000 g):
  - Proteina [PRO-001] Gallina criolla - 1500 g, $27000, 60 min
  - Tuberculo [TUB-001] Papa pastusa - 1000 g, $3000, 25 min
  - Tuberculo [TUB-002] Yuca - 800 g, $3500, 40 min
  - Verdura [VER-001] Mazorca - 600 g, $4000, 30 min
  - Verdura [VER-002] Plátano verde - 500 g, $4000, 30 min
  - Condimento [CON-001] Cilantro - 50 g, $1000, 5 min
  - Condimento [CON-002] Guascas - 20 g, $1000, 5 min

=== 2. Olla del sancocho trifásico ===
Olla (5450/8000 g):
  - Proteina [PRO-101] Gallina - 1000 g, $18000, 60 min
  - Proteina [PRO-102] Costilla de res - 1000 g, $26000, 90 min
  - Proteina [PRO-103] Cerdo - 800 g, $17600, 90 min
  - Tuberculo [TUB-101] Papa pastusa - 1000 g, $3000, 25 min
  - Tuberculo [TUB-102] Yuca - 1000 g, $3500, 40 min
  - Verdura [VER-101] Mazorca - 600 g, $4000, 30 min
  - Condimento [CON-101] Cilantro - 50 g, $1000, 5 min

=== 3. Olla pequeña (caldo de papa) ===
¿Cupo la yuca en la olla pequeña? false
Olla (830/1000 g):
  - Tuberculo [TUB-201] Papa criolla - 800 g, $4800, 25 min
  - Condimento [CON-201] Ajo - 30 g, $600, 20 min

=== 4. Sancochos ===
Sancocho [SAN-001] Sancocho de gallina - 8 porciones, 60 min, costo $45200, plato $9040
Sancocho [SAN-002] Sancocho trifásico - 10 porciones, 80500 min, costo $80500, plato $12880
Sancocho [SAN-003] Caldo de papa - 2 porciones, 25 min, costo $7900, plato $6320
¿El de gallina está completo? true
¿El caldo de papa está completo? false
¿El de gallina es trifásico? false
¿El trifásico es trifásico? true

=== 5. Pedidos en la fonda ===
Mesa 1: 2 x Sancocho de gallina + Arroz + Aguacate = $27080
Mesa 2: 3 x Sancocho trifásico + Arroz + Ají = $46140
¿Se registró el pedido de la mesa 3? false
¿Se registró el pedido de la mesa 4? false
Mesa 5: 6 x Sancocho de gallina = $54240
Pedidos registrados: 3
Porciones de gallina que quedan: 0
Ventas del día: $88260

=== 6. Polimorfismo ===
Buscar PRO-001: Gallina criolla (gallina)
Como Identificable: SAN-002
Tuberculo cuesta $3000
Sancocho cuesta $45200
Acompanamiento cuesta $2000
Pedido cuesta $27080