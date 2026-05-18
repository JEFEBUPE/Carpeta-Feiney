# Visor de Pruebas CPO-13 — PWA

App móvil instalable (PWA) para visualizar ensayos de pozos productores del bloque CPO-13.

## Configuración inicial

### 1. Crear proyecto Firebase
1. Ve a [console.firebase.google.com](https://console.firebase.google.com)
2. Crea un proyecto nuevo (ej. `cpo13-pruebas`)
3. Activa **Hosting** en el menú lateral
4. Copia el **Project ID** (ej. `cpo13-pruebas`)

### 2. Configurar el proyecto localmente
Edita `.firebaserc` y reemplaza `TU-PROYECTO-FIREBASE-ID` con tu Project ID:
```json
{ "projects": { "default": "cpo13-pruebas" } }
```

### 3. Configurar GitHub Secrets
En tu repositorio GitHub → Settings → Secrets and variables → Actions, agrega:

| Secret | Valor |
|--------|-------|
| `FIREBASE_SERVICE_ACCOUNT` | JSON de la cuenta de servicio de Firebase |
| `FIREBASE_PROJECT_ID` | Tu Project ID de Firebase |

Para obtener el JSON de la cuenta de servicio:
- Firebase Console → Configuración del proyecto → Cuentas de servicio → Generar nueva clave privada

### 4. Deploy manual (primera vez)
```bash
npm install -g firebase-tools
firebase login
firebase deploy
```

### 5. Deploy automático
Cada `git push` a la rama `main` despliega automáticamente vía GitHub Actions.

## Estructura
```
├── public/
│   ├── index.html       # App principal (PWA)
│   ├── manifest.json    # Configuración PWA
│   ├── sw.js            # Service Worker (modo offline)
│   └── icons/           # Iconos de la app
├── firebase.json        # Configuración Firebase Hosting
├── .firebaserc          # ID del proyecto Firebase
└── .github/workflows/
    └── firebase-deploy.yml  # CI/CD automático
```

## Instalar en móvil
1. Abre la URL de Firebase Hosting en Chrome (Android) o Safari (iOS)
2. En Android: menú → "Agregar a pantalla de inicio"
3. En iOS: compartir → "Agregar a pantalla de inicio"
4. En Chrome: aparece automáticamente el botón **📲 Instalar App**
