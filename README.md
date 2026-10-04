# Práctica: Integración Continua con GitHub Actions y Surge.sh

Este repositorio contiene la solución completa para la práctica de integración continua y despliegue automático hacia [Surge.sh](https://surge.sh) usando **GitHub Actions**.

---

## 🎯 Objetivo de la Tarea

1. **Crear repositorio local** con un archivo `index.html`.
2. **Crear el repositorio en GitHub** y conectar el origen remoto.
3. **Crear el workflow de GitHub Actions** en `.github/workflows/main.yaml`.
4. **Instalar Surge.sh** localmente.
5. **Configurar el Secret en GitHub** (`SURGE_TOKEN`) para no exponer credenciales públicamente.
6. **Validar la ejecución automática del pipeline** ante cada `git push` a la rama `main`.

---

## 📁 Estructura del Proyecto

```text
tarea-surge-ci/
├── .github/
│   └── workflows/
│       └── main.yaml      # Pipeline de CI/CD para GitHub Actions
├── index.html             # Página web a desplegar
└── README.md              # Documentación de la tarea
```

---

## ⚙️ Configuración del Secreto en GitHub

Para que GitHub Actions pueda publicar en tu cuenta de Surge sin pedir contraseña de manera interactiva:

1. Obtén tu token de Surge en la terminal ejecutando:
   ```bash
   surge token
   ```
2. En este repositorio en GitHub, ve a **Settings** > **Secrets and variables** > **Actions**.
3. Haz clic en **New repository secret**:
   - **Name:** `SURGE_TOKEN`
   - **Value:** *(Pega el token que te dio el comando anterior)*
4. (Opcional) Si deseas personalizar el subdominio de Surge, crea otro secret:
   - **Name:** `SURGE_DOMAIN`
   - **Value:** `tu-dominio-personalizado.surge.sh`
   *(Si no se define, el workflow usará `orlando-surge-ci.surge.sh` por defecto).*

---

## 🚀 Probar que todo funciona

Cada vez que se realiza un commit y push a la rama `main`:
```bash
git add .
git commit -m "feat: actualizacion de contenido"
git push origin main
```
El flujo de **GitHub Actions** se dispara automáticamente, instala Surge y publica la página en segundos.
