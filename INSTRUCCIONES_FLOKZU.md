# Instrucciones para configurar el Email Automático en Flokzu

## 📧 Template de Email Creado
Se ha creado el archivo `email_template_flokzu.html` que contiene el template completo para el correo automático.

## 🔧 Cómo configurar en Flokzu

### Paso 1: Acceder a la configuración del proceso
1. Ingresa a Flokzu
2. Ve al proceso "Ingreso y Salida de Equipos de Construcción"
3. Haz clic en "Editar proceso" o "Configuración"

### Paso 2: Agregar tarea de envío de email
1. En el diseñador de procesos, agrega una tarea de tipo "Enviar Email" o "Notificación"
2. Esta tarea debe ejecutarse automáticamente después de que se complete el formulario

### Paso 3: Configurar el email
1. **Destinatarios**: Puedes configurar los destinatarios de varias formas:
   - Usar los campos del formulario: `{{Mail Jefe de Taller}}` y `{{Mail Administrativo de Taller}}`
   - Agregar emails fijos (CC o BCC)
   - Combinar ambos

2. **Asunto del email**: 
   ```
   Registro de Equipo - {{Es un ingreso o una salida?}} - {{Denominación del Activo Fijo}}
   ```

3. **Cuerpo del email**: 
   - Copia todo el contenido del archivo `email_template_flokzu.html`
   - Pégalo en el editor HTML de Flokzu
   - Flokzu reemplazará automáticamente las variables `{{nombre_del_campo}}` con los valores del formulario

### Paso 4: Mapeo de campos
Asegúrate de que los nombres de los campos en Flokzu coincidan exactamente con los del template:

**Información del Movimiento:**
- `{{Es un ingreso o una salida?}}`
- `{{Fecha del ingreso}}`
- `{{Hora del ingreso}}`
- `{{Sucursal}}`
- `{{Cliente}}`
- `{{Nombre Jefe de Taller}}`
- `{{Mail Jefe de Taller}}`
- `{{Nombre Administrativo de Taller}}`
- `{{Mail Administrativo de Taller}}`

**Detalles del Equipo:**
- `{{Denominación del Activo Fijo}}`
- `{{Denominación del Activo Fijo (Que no se encuentra en Base de Datos)}}`
- `{{Número de Serie}}`
- `{{Número de Serie (Que no se encuentra en Base de Datos)}}`
- `{{Empresa}}`
- `{{Empresa (Escribir para registrar en la Base de Datos)}}`
- `{{Cantidad de Horas}}`
- `{{Nivel de combustible}}`

**Chequeo del Equipo (30 items):**
Para cada ítem del 1 al 30:
- Estado: `{{Nombre del campo de estado}}`
- Observación: `{{X. Detallar Observación}}`
- Imagen: `{{X. Imagen Observación}}`

### Paso 5: Probar el email
1. Guarda la configuración
2. Crea una instancia de prueba del proceso
3. Completa el formulario con datos de prueba
4. Verifica que el email se envíe correctamente y que todos los campos se muestren bien

## 📝 Notas importantes

1. **Variables de Flokzu**: Las variables deben estar entre dobles llaves `{{nombre_variable}}`
2. **Nombres exactos**: Los nombres de los campos deben coincidir exactamente (mayúsculas, espacios, etc.)
3. **Imágenes**: Las imágenes se adjuntarán automáticamente si Flokzu soporta archivos adjuntos en los campos
4. **Formato HTML**: El template usa HTML inline CSS para asegurar compatibilidad con clientes de email

## 🎨 Personalización

Si necesitas modificar el diseño:
- Los colores principales están en los estilos inline
- Verde claro: `#dff3e6` (fondo de secciones)
- Verde más oscuro: `#d4edda` (header)
- Puedes cambiar estos valores para ajustar la paleta de colores

## ⚠️ Solución de problemas

**Si los campos no se reemplazan:**
- Verifica que los nombres de los campos en Flokzu coincidan exactamente
- Asegúrate de estar usando el formato correcto `{{nombre_campo}}`

**Si el formato se ve mal:**
- Algunos clientes de email pueden no soportar ciertos estilos CSS
- El template usa estilos inline que son más compatibles

**Si las imágenes no aparecen:**
- Verifica que Flokzu esté configurado para incluir archivos adjuntos
- Puede que necesites configurar las imágenes como enlaces en lugar de adjuntos
