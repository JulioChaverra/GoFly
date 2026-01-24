# ✈️ FlightOnTime - Sistema de Predicción de Retrasos de Vuelos

> **¿Quieres probar el proyecto? Accede aquí:** 🔗 [FlightOnTime Demo](https://flightontime-frontend.railway.app)

---

## 🎯 Descripción del Proyecto

FlightOnTime es una plataforma completa para predicción de retrasos de vuelos utilizando:
- **Machine Learning** para análisis predictivo
- **Microservicios** para escalabilidad
- **Angular** para interfaz moderna
- **Java Spring Boot** para backend robusto

---

## 🌟 Características Principales

✅ **Predicción de Retrasos**  
Usa machine learning para predecir si un vuelo llegará a tiempo

✅ **Estadísticas de Vuelos**  
Análisis completo de patrones de puntualidad por aerolínea

✅ **Búsqueda de Rutas**  
Encuentra vuelos por aerolínea y visualiza detalles

✅ **Autenticación**  
Sistema seguro de login y registro

✅ **Interfaz Moderna**  
Diseño responsive con Angular y Tailwind CSS

---

## 🏗️ Arquitectura

```
┌─────────────────────────────────────────────────────────────┐
│                    FRONTEND (Angular)                       │
│              🌐 localhost:4200                              │
│           ↓              ↓              ↓                    │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌──────────────┐  ┌─────────────┐  ┌──────────────────┐   │
│  │   GATEWAY    │  │   EUREKA    │  │  CONFIG SERVER   │   │
│  │  :8080       │  │   :8761     │  │     :8888        │   │
│  └──────┬───────┘  └─────┬───────┘  └────────┬─────────┘   │
│         │                │                    │              │
│         ▼                ▼                    ▼              │
│  ┌──────────────────────────────────────────────────────┐   │
│  │   FLIGHT PREDICTION SERVICE                         │   │
│  │   - Predicción con ML                              │   │
│  │   - Gestión de vuelos                              │   │
│  │   - Estadísticas                                   │   │
│  │   :8090                                             │   │
│  └──────────────────────┬───────────────────────────────┘   │
│                         │                                    │
│                         ▼                                    │
│  ┌──────────────────────────────────────────────────────┐   │
│  │          MACHINE LEARNING SERVICE                    │   │
│  │   - Predicción con modelo entrenado                │   │
│  │   - FastAPI                                         │   │
│  │   :8000                                             │   │
│  └──────────────────────┬───────────────────────────────┘   │
│                         │                                    │
│                         ▼                                    │
│  ┌──────────────────────────────────────────────────────┐   │
│  │          DATABASE (MySQL)                            │   │
│  │   - Vuelos                                           │   │
│  │   - Usuarios                                         │   │
│  │   - Estadísticas                                     │   │
│  └──────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

---

## 🚀 Despliegue en la Nube

### Opción 1: Railway.app (Recomendado ⭐)

La forma más fácil de probar el proyecto online:

```bash
1. Conecta tu GitHub a Railway.app
2. Selecciona este repositorio
3. Railway detectará automáticamente los servicios
4. Espera 5-10 minutos
5. ¡Listo! Accede al link público
```

**Ventajas:**
- ✅ Free tier (500 horas/mes)
- ✅ Deploy automático en cada push
- ✅ Soporta Java, Python, Node.js
- ✅ Soporta MySQL/PostgreSQL
- ✅ Variables de entorno integradas

### Opción 2: Docker Compose (Local)

Para probar localmente con Docker:

```bash
docker-compose up --build
```

Accede a:
- Frontend: http://localhost:4200
- Gateway: http://localhost:8080
- Eureka: http://localhost:8761

### Opción 3: Desarrollo Local

Para desarrollo con Maven y npm:

```bash
# Terminal 1 - Config Server
cd FlightOnTime/config-server
mvn clean spring-boot:run

# Terminal 2 - Eureka
cd FlightOnTime/eureka
mvn clean spring-boot:run

# Terminal 3 - Flight Prediction
cd FlightOnTime/flight-prediction
mvn clean spring-boot:run

# Terminal 4 - Gateway
cd FlightOnTime/gateway
mvn clean spring-boot:run

# Terminal 5 - ML Service
cd microServicioML
pip install -r requirements.txt
uvicorn app:app --host 0.0.0.0 --port 8000

# Terminal 6 - Frontend
cd FlightOnTime-FrontEnd
npm install
npm start
```

---

## 📚 Documentación

- [DEPLOY_NUBE.md](DEPLOY_NUBE.md) - Guía completa de despliegue
- [QUICK_START.txt](QUICK_START.txt) - Guía rápida de inicio
- [docker-compose.yml](docker-compose.yml) - Configuración Docker

---

## 👥 Usuarios de Prueba

Para probar la plataforma, puedes:

1. **Registrarse**: Clic en "Registrarse" en la página de inicio
2. **Login**: Usar credenciales de prueba (si están disponibles)
3. **Explorar**: 
   - Ver vuelos disponibles
   - Ver predicciones de retrasos
   - Consultar estadísticas

---

## 🛠️ Tecnologías Utilizadas

### Backend
- **Java 17** - Lenguaje principal
- **Spring Boot 3.5.9** - Framework web
- **Spring Cloud** - Microservicios
- **Maven** - Build tool
- **MySQL 8.0** - Base de datos

### Servicios
- **Eureka** - Service Registry
- **Config Server** - Gestión centralizada de config
- **Gateway** - API Gateway

### Frontend
- **Angular** - Framework web
- **TypeScript** - Lenguaje
- **Tailwind CSS** - Estilos
- **npm** - Package manager

### ML & Data Science
- **Python** - Lenguaje
- **FastAPI** - Framework web
- **Scikit-learn** - Machine Learning
- **Pandas** - Análisis de datos

### DevOps
- **Docker** - Containerización
- **Docker Compose** - Orquestación local
- **Railway.app** - Cloud hosting

---

## 📊 Casos de Uso

### 1. Predicción de Retrasos
```
Entrada: Datos del vuelo (aerolínea, ruta, hora, clima)
↓
ML Model (scikit-learn)
↓
Salida: Predicción de retraso + probabilidad
```

### 2. Análisis de Estadísticas
```
Consultar: Vuelos por aerolínea
↓
Calcular: % puntual vs retrasado
↓
Visualizar: Gráficos en el dashboard
```

### 3. Búsqueda de Rutas
```
Buscar: Vuelos de una aerolínea
↓
Filtrar: Por fecha, origen, destino
↓
Mostrar: Detalles completos del vuelo
```

---

## 🔐 Seguridad

- ✅ Autenticación JWT
- ✅ Contraseñas hasheadas
- ✅ Variables de entorno para credenciales
- ✅ CORS configurado
- ✅ Validación de entrada

---

## 📈 Próximas Mejoras

- [ ] Integración con APIs reales de aerolíneas
- [ ] Notificaciones push de retrasos
- [ ] Historial de predicciones
- [ ] Análisis comparativo entre aerolíneas
- [ ] Mobile app (React Native)
- [ ] Caché distribuido (Redis)

---

## 👨‍💻 Autor

**Tu Nombre/Equipo**  
GitHub: [Tu Perfil](https://github.com)

---

## 📞 Contacto & Soporte

¿Preguntas o comentarios?
- 📧 Email: tu-email@example.com
- 💬 GitHub Issues: [Crear issue](https://github.com/tu-repo/issues)
- 🐛 Reportar bug: Abre un issue con descripción detallada

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Ver [LICENSE](LICENSE) para más detalles.

---

## 🙏 Agradecimientos

- Spring Cloud community
- Angular team
- FastAPI creators
- Railway.app equipo

---

## ⭐ ¿Te gusta el proyecto?

Si te resulta útil, considera:
- ⭐ Dar una estrella en GitHub
- 🔄 Compartir con otros
- 💬 Dejar feedback
- 🤝 Contribuir con mejoras

---

**Última actualización**: Enero 20, 2026  
**Versión**: 1.0  
**Estado**: ✅ En producción

---

### 🔗 Links Útiles

- 🌐 **Sitio en línea**: https://flightontime-frontend.railway.app
- 📚 **Documentación**: Ver archivos .md en este repositorio
- 🐳 **Docker Hub**: [flightontime-docker-hub](tu-docker-hub)
- 📊 **API Docs**: https://gateway-prod.railway.app/swagger-ui.html

---

**Hecho con ❤️ por el equipo de FlightOnTime**
