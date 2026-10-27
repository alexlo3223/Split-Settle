# Split & Settle

Web app para dividir gastos entre amigos. Inicio de sesión (Google o email), grupos compartidos en tiempo real, invitación por enlace. Funciona en PC y móvil. Sin servidor propio: es una página estática más Firebase (plan gratuito Spark).

## Puesta en marcha (unos 10 minutos)

1. Entra en https://console.firebase.google.com y crea un proyecto.
2. **Authentication > Comenzar > Método de acceso**: activa **Google** y **Correo electrónico/contraseña**.
3. **Firestore Database > Crear base de datos** (modo producción, la región que prefieras).
4. **Configuración del proyecto > Tus apps > Web (`</>`)**: registra la app y copia el objeto `firebaseConfig` en `firebase-config.js`.
5. Instala la CLI y despliega desde esta carpeta (necesita Node.js):

```bash
npm i -g firebase-tools
firebase login
firebase use --add        # elige tu proyecto
firebase deploy           # sube la web y las reglas de Firestore
```

Al terminar, la CLI muestra la URL (`https://tu-proyecto.web.app`). Esa es la dirección de la app: ábrela, entra, crea un grupo y pulsa **Invitar** para enviar el enlace a tus amigos.

## Probarla en tu equipo antes de subirla

Sírvela en local desde esta carpeta, por ejemplo con `npx serve .`, y abre `http://localhost:3000`. `localhost` ya está autorizado para el inicio de sesión, y los datos van a tu proyecto de Firebase real.

## Notas

- Las reglas (`firestore.rules`) hacen que solo los miembros de un grupo lean o escriban sus gastos y pagos. Para entrar hay que conocer el código del grupo.
- La app solo registra los pagos; no mueve dinero real.
- Para usar tu propio dominio: Firebase Hosting > Agregar dominio personalizado, y añádelo en Authentication > Configuración > Dominios autorizados.
