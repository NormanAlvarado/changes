# 🚀 Guía de Despliegue - Auth0 Express App

Este proyecto es una **aplicación de servidor backend** que requiere un entorno que soporte Node.js, no un sitio estático.

## ❌ **¿Por qué Netlify no funciona directamente?**

- **Tu app es un servidor Express** (backend)
- **Netlify hospeda sitios estáticos** (frontend)
- **Auth0 necesita un servidor** para manejar callbacks
- **No hay "build" porque no se compila**, se ejecuta directamente

## ✅ **Opciones de Despliegue Recomendadas**

### **1. Railway.app (Más fácil y moderno)**

```bash
# 1. Ve a https://railway.app
# 2. Conecta tu GitHub
# 3. Selecciona este repositorio
# 4. Configura las variables de entorno
# 5. ¡Deploy automático!
```

**Variables de entorno en Railway:**
- `AUTH0_SECRET`: tu_secreto_largo
- `AUTH0_CLIENT_ID`: E2hORy9j8koBxM8UPr5194AgFZ5UzSKA  
- `AUTH0_ISSUER_BASE_URL`: https://norman-alvarado.us.auth0.com
- `AUTH0_BASE_URL`: https://tu-app.railway.app

### **2. Heroku (Clásico y confiable)**

```bash
# Instalar Heroku CLI
# https://devcenter.heroku.com/articles/heroku-cli

# 1. Login a Heroku
heroku login

# 2. Crear app
heroku create tu-app-name

# 3. Configurar variables de entorno
heroku config:set AUTH0_SECRET="tu_secreto_largo"
heroku config:set AUTH0_CLIENT_ID="E2hORy9j8koBxM8UPr5194AgFZ5UzSKA"
heroku config:set AUTH0_ISSUER_BASE_URL="https://norman-alvarado.us.auth0.com"
heroku config:set AUTH0_BASE_URL="https://tu-app-name.herokuapp.com"

# 4. Deploy
git add .
git commit -m "Deploy to Heroku"
git push heroku main
```

### **3. Render.com (Alternativa moderna)**

```bash
# 1. Ve a https://render.com
# 2. Conecta tu GitHub
# 3. Selecciona "Web Service"
# 4. Configura:
#    - Build Command: npm install
#    - Start Command: npm start
# 5. Agrega variables de entorno
```

### **4. Vercel (Con funciones serverless)**

```bash
# Instalar Vercel CLI
npm i -g vercel

# Deploy
vercel

# Configurar variables de entorno en el dashboard
```

## 🔧 **Configuración Post-Despliegue**

### **1. Actualizar Auth0**

Una vez desplegado, actualiza tu aplicación Auth0:

- **Allowed Callback URLs**: `https://tu-dominio.com/callback`
- **Allowed Logout URLs**: `https://tu-dominio.com`
- **Allowed Web Origins**: `https://tu-dominio.com`

### **2. Actualizar .env en producción**

```env
AUTH0_BASE_URL=https://tu-dominio-de-produccion.com
# Resto de variables igual
```

## 📝 **Scripts Disponibles**

```bash
npm start        # Inicia el servidor
npm run dev      # Modo desarrollo  
npm run build    # Solo muestra mensaje (no hay build real)
```

## 🐛 **Solución de Problemas**

### **"Application error" en Heroku**
```bash
heroku logs --tail
# Revisa los logs para ver el error específico
```

### **Variables de entorno no definidas**
```bash
# Verifica que todas las variables estén configuradas
heroku config
# o en Railway/Render: revisa el dashboard
```

### **Error de CORS**
Asegúrate de que `AUTH0_BASE_URL` coincida exactamente con tu dominio de producción.

## 🎯 **Recomendación Final**

**Para principiantes**: Railway.app (más fácil)
**Para proyectos serios**: Heroku o Render
**Para integración con Vercel**: Usar funciones serverless

## 📚 **Recursos Útiles**

- [Railway.app Docs](https://docs.railway.app/)
- [Heroku Node.js Guide](https://devcenter.heroku.com/articles/getting-started-with-nodejs)
- [Render Deployment](https://render.com/docs/deploy-node-express-app)
- [Auth0 Production Checklist](https://auth0.com/docs/deploy/checklist)