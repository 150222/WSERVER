Para configurar un servidor **Windows Server** como un servidor **DHCP** (Dynamic Host Configuration Protocol), que asignará direcciones IP automáticamente a los dispositivos de tu red, sigue estos pasos:

### 1. Preparación inicial
Antes de comenzar, asegúrate de cumplir con los requisitos:
- Tener instalado **Windows Server 2016, 2019 o 2022**.
- Contar con una **dirección IP estática** en el servidor.
- Tener acceso de administrador en el servidor.

### 2. Instalar el rol de DHCP en Windows Server
1. **Abrir el Administrador del Servidor**: Haz clic en el menú de Inicio y selecciona **Administrador del Servidor**.
2. **Añadir roles y características**:
   - En el Administrador del Servidor, selecciona **Agregar roles y características**.
   - Avanza hasta llegar a la página de selección de roles.
3. **Seleccionar el rol de DHCP**:
   - Marca la opción **Servidor DHCP** y haz clic en **Siguiente** hasta llegar a la página de confirmación.
   - Haz clic en **Instalar** para iniciar la instalación.
   - Cuando finalice, haz clic en **Cerrar**.

4. **Configurar el rol DHCP**:
   - Después de la instalación, en el Administrador del Servidor, aparecerá una alerta amarilla en la esquina superior derecha indicando que es necesario completar la configuración de DHCP.
   - Haz clic en el icono de alerta y selecciona **Completar configuración de DHCP**.
   - En la ventana emergente, selecciona **Credenciales predeterminadas** y haz clic en **Confirmar**.
   - Cuando termine, selecciona **Cerrar**.

### 3. Configurar un ámbito DHCP
Un ámbito (scope) define el rango de direcciones IP que el servidor DHCP puede asignar a los dispositivos en la red.

1. **Abrir la Consola de administración DHCP**:
   - Ve a **Herramientas** > **DHCP** en el Administrador del Servidor.
2. **Crear un nuevo ámbito**:
   - En la consola de DHCP, haz clic derecho en **IPv4** (o **IPv6**, según sea el caso) y selecciona **Nuevo ámbito**.
3. **Asistente para nuevo ámbito**:
   - **Nombre del ámbito**: Ingresa un nombre descriptivo para el ámbito (por ejemplo, "Rango de IP para la red local").
   - **Rango de direcciones IP**:
     - Especifica el **rango de direcciones IP** que el servidor DHCP asignará a los clientes (por ejemplo, 192.168.1.100 a 192.168.1.200).
     - Define la **máscara de subred** (ej., 255.255.255.0 para redes locales).
   - **Exclusión de direcciones IP**:
     - Si tienes direcciones dentro del rango que no deseas asignar (por ejemplo, 192.168.1.150), agrégalas en **Agregar exclusión**.
   - **Duración del arrendamiento**:
     - Define cuánto tiempo pueden los dispositivos conservar una IP (predeterminado es 8 días).
   - **Configuración de opciones DHCP**:
     - Puedes configurar opciones adicionales, como la **Puerta de enlace predeterminada** (la IP de tu router), **DNS**, y **WINS** si lo necesitas.
4. **Finalizar**:
   - Revisa la configuración y haz clic en **Finalizar**.

### 4. Activar el ámbito DHCP
1. En la consola de DHCP, haz clic derecho en el ámbito que acabas de crear.
2. Selecciona **Activar** para que comience a asignar direcciones IP.

### 5. Configurar el cortafuegos de Windows
Para asegurarte de que el servidor DHCP funcione correctamente, verifica que el cortafuegos permita el tráfico DHCP:
1. Ve a **Panel de Control** > **Sistema y Seguridad** > **Firewall de Windows Defender** > **Configuración avanzada**.
2. Asegúrate de que las reglas de entrada y salida para DHCP estén habilitadas.

### 6. Verificar la configuración
1. En un cliente de red, configura la opción de IP en **Obtener una dirección IP automáticamente**.
2. Conéctalo a la red y comprueba si recibe una IP del servidor DHCP.

Con estos pasos, tu **Windows Server** debería estar funcionando como un servidor **DHCP** en la red, asignando IP automáticamente a los dispositivos que se conecten.
