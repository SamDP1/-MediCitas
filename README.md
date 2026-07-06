# MediCitas — App completa con POO y patrones

Aplicación web funcional para la gestión de citas médicas de una clínica de atención general. Esta versión mantiene una interfaz más limpia y profesional: la app ya no muestra una pantalla técnica de explicación de POO o patrones; esa sustentación queda documentada aquí y en el código.

El proyecto cumple con la rúbrica solicitada:

- Paradigma de Orientación a Objetos.
- Mínimo 2 patrones de diseño.
- Interfaz gráfica funcional.
- Manejo de excepciones.

No necesita instalar librerías externas. Funciona solo con HTML, CSS y JavaScript.

---

## Cómo abrirla

### Opción rápida

1. Descomprime el archivo ZIP.
2. Entra a la carpeta `MediCitas_App_Completa`.
3. Da doble clic en `index.html`.
4. Se abrirá en el navegador.

### Opción recomendada

Esta opción es mejor si quieres probar notificaciones del navegador.

1. Descomprime el archivo ZIP.
2. Abre una terminal dentro de la carpeta `MediCitas_App_Completa`.
3. Ejecuta:

```bash
python -m http.server 8000
```

4. Abre en el navegador:

```text
http://localhost:8000
```

---

## Cuentas demo

- Administrador: `admin@medicitas.com` / `admin123`
- Recepcionista: `recepcion@medicitas.com` / `recep123`
- Paciente: `ana@medicitas.com` / `paciente123`
- Paciente: `carlos@medicitas.com` / `paciente123`
- Médico: `smith@medicitas.com` / `medico123`
- Médico: `ramos@medicitas.com` / `medico123`

---

## Cambios visuales de esta versión

Se retiró la sección visible **“POO y patrones”** del menú para que el sistema se vea más natural como una app médica real.

También se limpió la pantalla de inicio de sesión. Ahora muestra una descripción general del sistema y módulos funcionales, sin mencionar directamente nombres técnicos como patrones de diseño o excepciones.

La implementación técnica sigue dentro del código y se explica en este README.

---

## Funciones principales de la app

- Login por correo y contraseña.
- Control de acceso por roles.
- Roles: administrador, recepcionista, paciente y médico.
- Crear, editar, confirmar y cancelar citas.
- Evitar duplicidad de horarios.
- Bloquear horarios médicos.
- Registrar pacientes.
- Crear cuentas nuevas.
- Activar o desactivar cuentas.
- Ver agenda médica.
- Ver historial del paciente.
- Buscar información por módulos.
- Recibir notificaciones internas.
- Simular envío SMS.
- Ver logs de trazabilidad.
- Exportar logs en JSON.
- Cambiar la política de asignación de horarios.
- Restaurar datos demo.
- Persistencia con `localStorage`.

---

## Orientación a Objetos

Se agregaron clases explícitas en `app.js` para organizar el dominio del sistema:

- `Usuario`
- `Paciente`
- `Medico`
- `Cita`
- `CitaConsulta`
- `CitaTelemedicina`
- `CitaLaboratorio`

Estas clases permiten sustentar el paradigma de Orientación a Objetos porque agrupan atributos y comportamientos propios de cada entidad. Por ejemplo, `Usuario` valida permisos, `Paciente` administra historial y `Cita` permite cambiar su estado.

---

## Manejo de excepciones

Se agregaron excepciones personalizadas:

- `MediCitasException`
- `ValidacionException`
- `AccesoNoPermitidoException`
- `EntidadNoEncontradaException`
- `EstadoInvalidoException`
- `HorarioOcupadoException`

Además, la app usa `App.handleError(err)` como manejador central. Esto permite capturar errores, mostrar mensajes al usuario y registrar eventos críticos sin que la aplicación se caiga.

---

## Patrones de diseño implementados

La rúbrica pide al menos 2 patrones. Esta versión implementa más de 2:

### 1. Factory Method

Ubicación principal: `CitaFactory.create(cita)`.

Sirve para crear el objeto correcto según el tipo de cita seleccionado:

- `CitaConsulta`
- `CitaTelemedicina`
- `CitaLaboratorio`

Así, el formulario no necesita saber qué clase concreta debe construir.

### 2. Strategy

Ubicación principal: `Strategy.assign(...)`.

Permite cambiar la política de asignación automática de horarios sin modificar el formulario de citas.

Estrategias disponibles:

- Por disponibilidad.
- Por urgencia.
- Por orden de llegada.

### 3. Observer

Ubicación principal: `Observer.notifyAppointment(...)`.

Cuando una cita se crea, modifica, confirma o cancela, el sistema notifica automáticamente a los usuarios relacionados.

### 4. Adapter

Ubicación principal: `SMSAdapter.send(...)`.

Simula el envío de SMS y deja preparada la estructura para reemplazar ese envío por un proveedor real en el futuro.

---

## Diagrama de clases

Se incluye el archivo:

```text
DIAGRAMA_CLASES_MediCitas.puml
```

Ese archivo contiene un diagrama de clases en PlantUML. Puedes pegarlo en PlantUML para generar la imagen del diagrama.

---

## Qué decir en la sustentación

Puedes decir esto:

> MediCitas es un sistema web de gestión de citas médicas desarrollado con JavaScript, HTML y CSS. El proyecto aplica Programación Orientada a Objetos mediante clases como Usuario, Paciente, Médico y Cita. Además, implementa patrones de diseño como Factory Method para crear distintos tipos de cita, Strategy para cambiar la asignación de horarios, Observer para las notificaciones y Adapter para simular el envío de SMS. También incluye manejo de excepciones personalizadas y un manejador central de errores para evitar fallos inesperados en la aplicación.

---

## Nota importante

Si haces cambios y luego quieres volver a los datos iniciales, usa el botón **Restaurar datos demo** en el login. La información se guarda en el navegador mediante `localStorage`.
