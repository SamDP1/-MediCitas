# MediCitas — App completa reforzada para POO

Aplicación web funcional de gestión de citas médicas. Esta versión fue complementada para cumplir con una rúbrica basada en:

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

## Qué ya tenía la app

La app ya incluía:

- Inicio de sesión con correo y contraseña.
- Roles: administrador, recepcionista, paciente y médico.
- Gestión de citas médicas.
- Registro de pacientes.
- Agenda médica.
- Bloqueo de horarios por médico.
- Historial del paciente.
- Notificaciones internas.
- SMS simulado.
- Trazabilidad y logs.
- Alertas predictivas.
- Persistencia con `localStorage`.

---

## Qué se agregó o reforzó en esta versión

### 1. Orientación a Objetos más clara

Se agregaron clases explícitas en `app.js`:

- `Usuario`
- `Paciente`
- `Medico`
- `Cita`
- `CitaConsulta`
- `CitaTelemedicina`
- `CitaLaboratorio`

Estas clases ayudan a sustentar que el proyecto usa POO, porque organizan entidades, atributos y comportamientos.

### 2. Excepciones personalizadas

Se agregaron clases de excepción:

- `MediCitasException`
- `ValidacionException`
- `AccesoNoPermitidoException`
- `EntidadNoEncontradaException`
- `EstadoInvalidoException`
- `HorarioOcupadoException`

También se agregó `App.handleError(err)` como manejador central de errores. Esto evita que la aplicación se caiga y permite mostrar el error de forma clara al usuario.

### 3. Pantalla “POO y patrones”

Se agregó una nueva sección en el menú llamada **POO y patrones**. Allí se explica dentro de la misma app:

- Qué clases usa el proyecto.
- Qué patrones de diseño se implementaron.
- Dónde se usa cada patrón.
- Cómo fluye una cita desde la interfaz hasta las notificaciones.

Esta pantalla sirve como evidencia rápida para exposición o revisión del docente.

### 4. Diagrama PlantUML

Se agregó el archivo:

```text
DIAGRAMA_CLASES_MediCitas.puml
```

Ese archivo contiene un diagrama de clases en código PlantUML para poder pegarlo en PlantUML y generar la imagen.

---

## Patrones de diseño implementados

La rúbrica pide al menos 2 patrones. Esta versión contiene más de 2:

### Factory Method

Usado en `CitaFactory.create(cita)`.

Sirve para crear diferentes tipos de citas según el tipo seleccionado:

- Consulta general.
- Telemedicina.
- Laboratorio.

### Strategy

Usado en `Strategy.assign(...)`.

Permite cambiar la política de asignación automática de horarios:

- Por disponibilidad.
- Por urgencia.
- Por orden de llegada.

### Observer

Usado en `Observer.notifyAppointment(...)`.

Cuando una cita cambia, se notifican automáticamente los usuarios relacionados.

### Adapter

Usado en `SMSAdapter.send(...)`.

Simula el envío de SMS y deja lista la estructura para conectarla después con un proveedor real.

---

## Funciones principales

- Login por correo y contraseña.
- Control de acceso por roles.
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
- Cambiar estrategia de asignación de horarios.
- Restaurar datos demo.

---

## Nota importante

Si haces cambios y luego quieres volver a los datos iniciales, usa el botón **Restaurar datos demo** en el login. La información se guarda en el navegador mediante `localStorage`.
