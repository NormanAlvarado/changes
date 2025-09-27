# 🚀 GUÍA RÁPIDA DE DESPLIEGUE

## ✅ **Tu proyecto está listo para desplegar!**

### **1. Railway.app (Recomendado - Más fácil)**

1. Ve a [railway.app](https://railway.app)
2. Conecta con GitHub
3. Selecciona este repositorio 
4. Configura estas variables de entorno:
   ```
   AUTH0_SECRET=ensBA81lDjHGBA-VQru53lvcP71f8sj2uDy4fCADUQTQ3sbVhGL_JOo5v6I4Tggs
   AUTH0_CLIENT_ID=E2hORy9j8koBxM8UPr5194AgFZ5UzSKA
   AUTH0_ISSUER_BASE_URL=https://norman-alvarado.us.auth0.com
   AUTH0_BASE_URL=https://tu-app.railway.app
   ```
5. ¡Deploy automático!

### **2. Heroku (Clásico)**

```bash
# Instalar Heroku CLI primero: https://devcenter.heroku.com/articles/heroku-cli
heroku login
heroku create tu-app-name

# Variables de entorno
heroku config:set AUTH0_SECRET="ensBA81lDjHGBA-VQru53lvcP71f8sj2uDy4fCADUQTQ3sbVhGL_JOo5v6I4Tggs"
heroku config:set AUTH0_CLIENT_ID="E2hORy9j8koBxM8UPr5194AgFZ5UzSKA"  
heroku config:set AUTH0_ISSUER_BASE_URL="https://norman-alvarado.us.auth0.com"
heroku config:set AUTH0_BASE_URL="https://tu-app-name.herokuapp.com"

# Deploy
git push heroku main
```

### **3. Render.com**

1. Ve a [render.com](https://render.com)
2. New > Web Service
3. Conecta este repo
4. Configuración:
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
5. Agrega las variables de entorno (mismas de Railway)

## 🔧 **Después del despliegue**

### **Actualizar Auth0:**
Ve a tu [Dashboard de Auth0](https://manage.auth0.com) y actualiza:

- **Allowed Callback URLs**: `https://tu-dominio.com/callback`
- **Allowed Logout URLs**: `https://tu-dominio.com` 
- **Allowed Web Origins**: `https://tu-dominio.com`

### **Probar la app:**
- `https://tu-dominio.com/` → Debe mostrar "Logged out"
- `https://tu-dominio.com/login` → Redirige a Auth0
- `https://tu-dominio.com/dashboard` → Requiere login

## 📋 **Checklist Pre-Despliegue**

- ✅ Git configurado y commit realizado
- ✅ Variables de entorno preparadas  
- ✅ Archivos de configuración creados (Procfile, railway.json, etc.)
- ✅ `.env` en .gitignore (no se subirá al repo)
- ✅ Script de build agregado

## 🆘 **¿Problemas?**

1. **"Application error"**: Revisa los logs de la plataforma
2. **Auth0 no funciona**: Verifica las URLs de callback
3. **Variables no definidas**: Asegúrate de configurarlas en el dashboard

**Tu proyecto está 100% listo para desplegar! 🎉**