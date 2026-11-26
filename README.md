# Amigo Secreto Familiar

Página para el amigo secreto de la familia: cada uno entra con Google, escribe su lista de regalos con comentarios, y el organizador hace el sorteo.

- `index.html`: la página (para GitHub Pages)
- `firebase-config.js`: datos de tu proyecto de Firebase y quién organiza
- `firestore.rules`: reglas de seguridad de la base de datos
- `gifs/`: los gatitos navideños
- `amigo-secreto.html`: la versión publicada en Claude (no se usa en GitHub Pages)

## Configuración (una sola vez, ~15 minutos)

### 1. Crear el proyecto en Firebase
1. Entra a https://console.firebase.google.com y crea un proyecto (Google Analytics no hace falta).
2. **Authentication** > Comenzar > pestaña *Sign-in method* > activa **Google**.
3. **Firestore Database** > Crear base de datos > modo producción > elige una región cercana (por ejemplo `southamerica-east1`).
4. **Configuración del proyecto** (engranaje) > *Tus apps* > ícono web `</>` > registra la app (sin Hosting). Copia los valores de `firebaseConfig` en `firebase-config.js`.

### 2. Publicar en GitHub Pages
1. Sube esta carpeta a un repositorio de GitHub.
2. En el repositorio: **Settings > Pages** > *Deploy from a branch* > rama `main`, carpeta `/ (root)`.
3. Tu página queda en `https://TU-USUARIO.github.io/NOMBRE-DEL-REPO/`.
4. En Firebase: **Authentication > Settings > Authorized domains** > agrega `TU-USUARIO.github.io`.

### 3. Hacerte organizador
1. Abre la página y entra con Google. Arriba aparece un aviso con tu código (UID).
2. Pega ese UID en `firebase-config.js` (`ADMIN_UIDS`) y en `firestore.rules` (función `isAdmin`).
3. En Firebase: **Firestore Database > Reglas**, pega el contenido de `firestore.rules` y pulsa **Publicar**.
4. Sube el cambio de `firebase-config.js` a GitHub y recarga la página: aparece la pestaña **Organizar**.

### 4. Invitar a la familia
Mándales el enlace de GitHub Pages por WhatsApp. Cada uno entra con su cuenta de Google, escribe su nombre y su lista. Cuando estén todos, haz el sorteo en **Organizar**.

## Bueno saber
- Cualquiera con el enlace y una cuenta de Google puede anotarse. Si se mete alguien que no es de la familia, quítalo desde **Organizar**.
- La página nunca muestra el sorteo de los demás, pero el organizador sí podría verlo mirando la base de datos en la consola de Firebase.
- El plan gratuito de Firebase (Spark) alcanza de sobra para una familia.
- Los GIFs vienen de Tenor.
