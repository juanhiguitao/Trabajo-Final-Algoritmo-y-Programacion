## 🎬 Manual de Usuario – CineLab UDEA
### 📘 Descripción General

El sistema de gestión CineLab UDEA es una aplicación desarrollada en Python que permite administrar funciones de cine del fin de semana dentro de un entorno académico.

El sistema permite:

- Registrar usuarios con validaciones.

- Mostrar la cartelera del fin de semana.

- Gestionar reservas de sillas en salas 11×11.

- Cancelar reservas.

- Generar facturas de compra.

- Acceder a reportes administrativos mediante credenciales.

- Visualizar disponibilidad de funciones y salas.

- Fue diseñado para ser práctico, fácil de operar y comprensible para estudiantes.

### 🖥 Requisitos del Sistema
Software necesario

- Python 3.8 o superior

Entorno recomendado 
- Google Colab o cualquier IDE con soporte para Python

Sistema operativo

- Windows / MacOS / Linux / Chromebook

Memoria

- 512 MB RAM o más (cualquier PC actual lo soporta)

Espacio en disco

- 50 MB libres para archivos y CSV opcionales

### 📚 Librerías requeridas

El sistema usa únicamente librerías estándar de Python:

- datetime → generación de fechas para reservas

- csv → exportación de datos (opcional)

- os → validaciones básicas del entorno

(No requiere instalaciones adicionales.)

### ⚙️ Instalación
✔ Opción recomendada: Google Colab

1. Abrir: https://colab.research.google.com

2. Crear un nuevo cuaderno.

3. Copiar y pegar todo el código de CineLab en una celda.

4. Ejecutar con Shift + Enter.

✔ Opción local (Python PC)

1. Descargar Python desde https://python.org

2. Instalar marcando: “Add Python to PATH”

3. Crear una carpeta, por ejemplo CineLabUDEA.

4. Guardar el archivo main.py dentro.

5. Abrir consola y ejecutar:
```python
cd CineLabUDEA
python main.py
```

### 🎥 Inicio del Sistema

Al ejecutar el programa, aparece el menú principal:
```python
====================================
           C I N E L A B  
              U D E A
        Sistema de Reservas
====================================

1. Registrar Usuario
2. Registrar Reserva
3. Cancelar Reserva
4. Consultar Funciones Fin de Semana
5. Administrador
6. Salir
====================================
```

### ⭐ Funcionalidades del Sistema
### 1️⃣ Registrar Usuario

Este módulo permite ingresar un nuevo usuario al sistema. Antes de realizar una reserva, el usuario debe estar registrado.

Datos requeridos

- Nombre: mínimo 3 letras, solo texto

- Apellido: mínimo 3 letras, solo texto

- Documento: entre 3 y 15 dígitos, solo números

- Tipo de vínculo:

  - Estudiante → $7.500

  - Docente → $10.000

  - Administrativo → $8.500

  - Oficial interno → $7.000

  - Público externo → $15.000

Errores comunes

- Nombre con números → ❌ “Juan123”

- Documento con letras → ❌ “12A45”

- Documento demasiado corto o largo

- Usuario ya existe (documento registrado previamente)

### 2️⃣ Registrar Reserva

Permite comprar un tiquete y seleccionar un asiento.

Pasos:

1. Seleccionar la opción “Registrar Reserva”.

2. Ingresar documento del usuario (ya debe estar registrado).

3. Elegir una de las funciones disponibles del fin de semana.

4. Ver el mapa de asientos (11×11):

```python
0 = disponible  
X = ocupado  
(Filas A–K, Columnas 1–11)
```

Ejemplo visual:

```python
A1 A2 A3 … A11
B1 B2 B3 … B11
…
K1 K2 K3 … K11
```

5. Seleccionar asiento (ej: “C7”).

6. Confirmar compra.

7. Se genera una factura en pantalla.

Factura ejemplo

```python
===============================
        FACTURA CINE UDEA
===============================

Nombre: Juan Pérez
Documento: 12345678
Película: Interstellar
Día: Sábado
Hora: 4:00pm
Asiento: B5
Precio: $7.500

Gracias por tu compra.
===============================
```
### 3️⃣ Cancelar Reserva

Permite que un usuario elimine una reserva realizada.

Pasos:

1. Ingresar documento.

2. El sistema muestra todas sus reservas.

3. Elegir cuál desea cancelar.

4. El asiento vuelve a quedar disponible (“0”).

5. Se confirma la cancelación.

Errores comunes

- Documento sin reservas existentes.

- Selección inválida de índice.

### 4️⃣ Consultar Funciones del Fin de Semana

Muestra la programación completa:

Funciones disponibles (fijas)

- 2:00pm → Interstellar

- 4:00pm → Oppenheimer

- 6:00pm → The Imitation Game

Para los días:

- Viernes

- Sábado

- Domingo

Muestra cuántos asientos libres quedan por función.

Ejemplo:
```python
Sábado – 4:00pm – Oppenheimer → 89 asientos disponibles
```
### 5️⃣ Módulo Administrador

Acceso restringido:
```python
Usuario: admin
Contraseña: 1234
```
Reportes disponibles

- Total de reservas registradas

- Total de tiquetes vendidos

- Total de ingresos

- Promedio de ventas por día

- Lista de usuarios registrados

- Usuario con más reservas

- Usuario con menos reservas (>0)

Este módulo es para control académico y análisis del uso del sistema.

### 6️⃣ Salir del Sistema

Termina la ejecución del programa.

### 🧩 Solución de Problemas
❌ “Nombre inválido”

- Debe tener al menos 3 letras

- No puede contener números

❌ “Documento inválido”

- Solo números

- Entre 3 y 15 dígitos

❌ “Usuario no registrado”

- Se debe registrar antes de reservar

❌ “Asiento inválido”

- Debe ser A–K + 1–11

- Ejemplo válido: D10

❌ “Asiento ocupado”

- Seleccionar otro disponible

❌ “Credenciales incorrectas” (administrador)

- Usar exactamente: admin / 1234

### 🧠 Buenas Prácticas
Para operadores:

- Registrar usuarios antes de reservar.

- Verificar datos antes de confirmar compras.

- Mantener orden al seleccionar asientos.

Para administradores:

- Revisar reportes semanalmente.

- Proteger las credenciales de acceso.

- Exportar CSV si es necesario para respaldo.

### 🎓 Capacidades del Sistema

- Manejo de usuarios ilimitados

- 9 funciones disponibles (3 por día × 3 días)

- Salas de 121 asientos cada una

- Facturación automática

- Reportes administrativos integrados

### ⚠️ Limitaciones

- No guarda datos entre ejecuciones (a menos que se habilite CSV).

- No tiene interfaz gráfica (todo es consola).

- Solo maneja funciones del fin de semana.

### 🏫 Contacto y Soporte

Universidad de Antioquia – Facultad de Ingeniería
Asignatura: Algoritmia y Programación
Proyecto: Sistema de Gestión CineLab UDEA

Desarrolladores: 
- Juan Felipe Higuita Ortiz 
- Juan Diego Tabares Gaviria

Versión del sistema: 1.3

Última actualización: noviembre 2025