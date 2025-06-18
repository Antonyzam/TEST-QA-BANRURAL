# Estrategia de Pruebas – Juego "Adivina tu número"

## Objetivo
Verificar que la aplicación funcione de acuerdo a los requisitos del negocio y asegurar que sea completamente funcional para el usuario final.

## Herramientas Utilizadas
- Navegador web (Chrome)
- Consola del navegador (F12)
- Pruebas manuales
- Validaciones de alertas y mensajes de estado

## Requisitos Funcionales del Juego

- El número a adivinar debe estar entre 1 y 100 (enteros).
- El usuario debe tener un máximo de 10 intentos para adivinar el número.
- Si el número ingresado no es un número entero, debe mostrar una alerta y **no contar como intento**.
- Mensajes visuales deben indicarle al usuario si el número es mayor o menor al número secreto.
- Al ganar: mostrar mensaje verde.
- Al perder: mostrar mensaje rojo.
- El diseño debe ser moderno, claro e intuitivo para el usuario final.

------------------------------------------------------------------------

## Casos de prueba
### 1. Validación de tipo de dato
**Prueba:** Ingresar texto o símbolos (ejemplo"abc", "#@!")  
**Resultado esperado:** Mostrar alerta y no contar como intento.  
**Resultado:** No había validación.  
**Solución aplicada:** Se agregó validación con `Number.isInteger()` y `parseInt`.

---

### 2. Número mayor o menor al número secreto
**Prueba:** Ingresar un número mayor o menor.  
**Resultado esperado:** Mostrar mensaje "¡Incorrecto! El número es mayor/menor!"  
**Resultado:** El mensaje no aparecía.  
**Solución aplicada:** Se corrigió la lógica condicional y se mostraron los mensajes adecuados con color negro.

---

### 3. Adivinar el número en menos de 10 intentos
**Prueba:** Adivinar el número correcto.  
**Resultado esperado:** Mostrar mensaje "¡Felicitaciones! Adivinaste el número!" en color verde.  
**Resultado:**  El mensaje no aparecía.
**Solución aplicada:** Se corrigió y ya se muestra el mensaje.

---

### 4. Agotar los 10 intentos sin acertar
**Prueba:** Ingresar números incorrectos hasta llegar a 10 intentos.  
**Resultado esperado:** Mostrar mensaje "¡¡¡Pérdistes!!!" en color rojo.  
**Resultado:** El contador no funcionaba.  
**Solución aplicada:** Se corrigió el conteo de intentos y el control de flujo.

---

## Conclusión
Se corrigieron todas las fallas encontradas en consola y mediante pruebas manuales. El archivo `index.html` actualizado es funcional y cumple con todos los requisitos del cliente.

---

## errores encontrados y correcciones

### 1. El número aleatorio generado estaba incorrecto

**Problema:**  let randomNumber = Math.random() * 10;

**correccion**  let randomNumber = Math.floor(Math.random() * 100) + 1;

### 2. guessSubmit.addeventListener no funcionaba

**Problema:**   guessSubmit.addeventListener('click', checkGuess);

**correccion**  guessSubmit.addEventListener('click', checkGuess);

### 3. Selección de clase incorrecta para mostrar pista

**Problema:** const lowOrHi = document.querySelector('lowOrHi');

**correccion** const lowOrHi = document.querySelector('.lowOrHi');

### 4. Lógica invertida en mensaje de victoria/derrota

**Problema:** El mensaje de "Felicitaciones" se mostraba al fallar, y el de "¡Pérdistes!" al acertar.

**correccion** Se reorganizó correctamente el bloque condicional:
if(userGuess === randomNumber) {
  // Felicitaciones (verde)
} else if(guessCount === ATTEMPTS) {
  // Perdiste (rojo)
}

### 5. Validación de número entero ausente

**Problema:** El juego aceptaba letras o caracteres no válidos, y seguía contando como intento.

**correccion** Se agregó validación con isNaN y Number.isInteger:
if (isNaN(userGuess) || !Number.isInteger(userGuess)) {
  alert(" Ingresa un número entero válido.");
  return;
}

### 6. Mejpra de experiencia visual

# Implementaciones:

-Se añadió CSS moderno: bordes redondeados, colores vivos, responsividad.

-Mensajes más claros e íconos visuales (🎯 ❌ 🔄 etc.).

-Se organizó el contenido dentro de un contenedor central .container para mejor presentación.

-Se añadió feedback visual para los intentos previos y resultados.

### Resultado del Testeo

| Escenario              | Resultado                           |
| ---------------------- | ----------------------------------- |
| Número fuera de rango  | ✓  Rechazado correctamente          |
| Entrada vacía o letras | ✓  Muestra alerta y no suma intento |
| Usuario gana           | ✓  Mensaje verde correcto           |
| Usuario pierde         | ✓  Mensaje rojo correcto            |
| Lógica menor/mayor     | ✓  Correcta                         |
| Reiniciar juego        | ✓  Funciona bien                    |
| Diseño                 | ✓  Intuitivo, moderno y atractivo   |


### Recomendaciones Finales

-Añadir almacenamiento de puntajes o estadísticas en localStorage (opcional).

-Mejorar accesibilidad (por ejemplo: navegación por teclado).

-Crear un login para ingresar al usuario.
