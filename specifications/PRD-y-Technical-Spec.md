# Sistema de Reservas de Canchas de Futbolito
## Especificación Técnica Completa y PRD

**Fecha de Creación:** 26 de Septiembre, 2025  
**Versión:** 1.0  
**Estado:** Listo para Implementación

---

## 1. Resumen Ejecutivo y Objetivos (PRD)

### 1.1 Problema a Resolver
El establecimiento de futbolito enfrenta un problema crítico con **reservas falsas** que genera pérdidas económicas y operativas. Los clientes realizan reservas sin datos verificables y posteriormente no se presentan, dejando canchas vacías que pudieron ser utilizadas por otros clientes.

### 1.2 Solución Propuesta
Sistema web de reservas en línea que requiere:
- **Identificación real del cliente** con datos verificables
- **Pago parcial o total por adelantado** para garantizar la reserva
- **Gestión automatizada** de horarios y disponibilidad

### 1.3 Objetivos de Negocio
- **Eliminar reservas falsas** en un 95%
- **Aumentar la confiabilidad** de las reservas
- **Mejorar la experiencia del cliente** con reservas instantáneas
- **Automatizar la gestión** de canchas y horarios
- **Incrementar ingresos** mediante pagos garantizados

### 1.4 Métricas de Éxito
- Reducción de no-shows del 40% actual al 5%
- 100% de reservas con pago confirmado
- Tiempo de reserva reducido de 10+ minutos (telefónica) a 3 minutos (online)

---

## 2. Historias de Usuario (User Stories) y Requisitos Funcionales

### 2.1 Historias de Usuario - Cliente

**HU-001: Registro de Usuario**
- Como un **cliente nuevo**, quiero **registrarme en el sistema** para **poder realizar reservas verificadas**
- **Criterios de Aceptación:**
  - Registro con nombre completo, teléfono, email y documento de identidad
  - Validación de email obligatoria
  - Verificación de unicidad de email y documento

**HU-002: Autenticación**
- Como un **cliente registrado**, quiero **iniciar sesión de forma segura** para **acceder a mis reservas**
- **Criterios de Aceptación:**
  - Login con email/teléfono y contraseña
  - Recuperación de contraseña por email
  - Sesión persistente con opción de logout

**HU-003: Visualización de Disponibilidad**
- Como un **cliente**, quiero **ver las canchas disponibles en tiempo real** para **seleccionar la mejor opción**
- **Criterios de Aceptación:**
  - Calendario visual con 6 canchas
  - Horarios de 8:00 AM a 10:00 PM
  - Bloques de 1h, 1.5h y 2h claramente diferenciados
  - Estados: Disponible, Ocupado, Mantenimiento

**HU-004: Realizar Reserva**
- Como un **cliente**, quiero **reservar una cancha** para **garantizar mi tiempo de juego**
- **Criterios de Aceptación:**
  - Selección de cancha, fecha, hora y duración
  - Cálculo automático del precio total
  - Confirmación de datos antes del pago

**HU-005: Procesamiento de Pago**
- Como un **cliente**, quiero **pagar mi reserva de forma segura** para **confirmar mi reserva**
- **Criterios de Aceptación:**
  - Opción de pago 50% inicial + 50% presencial
  - Opción de pago 100% en línea
  - Integración con pasarela de pagos segura
  - Recibo de pago por email

**HU-006: Gestión de Mis Reservas**
- Como un **cliente**, quiero **ver y gestionar mis reservas** para **controlar mis actividades**
- **Criterios de Aceptación:**
  - Lista de reservas activas y historial
  - Detalles completos de cada reserva
  - Opción de cancelación según políticas
  - Recordatorios automáticos

### 2.2 Historias de Usuario - Administrador

**HU-007: Dashboard Administrativo**
- Como un **administrador**, quiero **ver el estado general del sistema** para **tomar decisiones operativas**
- **Criterios de Aceptación:**
  - Vista general de ocupación diaria
  - Métricas de ingresos y reservas
  - Alertas de problemas técnicos

**HU-008: Gestión de Canchas**
- Como un **administrador**, quiero **gestionar la disponibilidad de canchas** para **optimizar las operaciones**
- **Criterios de Aceptación:**
  - Marcar canchas en mantenimiento
  - Ajustar horarios especiales
  - Configurar precios por bloque de tiempo

**HU-009: Gestión de Reservas**
- Como un **administrador**, quiero **supervisar todas las reservas** para **garantizar el servicio**
- **Criterios de Aceptación:**
  - Lista completa de reservas por fecha
  - Búsqueda por cliente o número de reserva
  - Capacidad de cancelar/modificar reservas

**HU-010: Gestión de Clientes**
- Como un **administrador**, quiero **gestionar la base de clientes** para **mantener datos actualizados**
- **Criterios de Aceptación:**
  - Lista de clientes registrados
  - Historial de reservas por cliente
  - Capacidad de bloquear clientes problemáticos

---

## 3. Requisitos No Funcionales

### 3.1 Rendimiento
- **Tiempo de respuesta:** < 2 segundos para consultas de disponibilidad
- **Tiempo de carga:** < 3 segundos para la página principal
- **Procesamiento de pagos:** < 10 segundos
- **Concurrencia:** Soporte para 50 usuarios simultáneos mínimo

### 3.2 Escalabilidad
- **Crecimiento de usuarios:** Sistema debe soportar hasta 1,000 usuarios registrados
- **Reservas diarias:** Hasta 100 reservas por día
- **Almacenamiento:** Crecimiento de 1GB anual estimado

### 3.3 Seguridad
- **Encriptación:** HTTPS obligatorio en toda la aplicación
- **Datos personales:** Cumplimiento con regulaciones de protección de datos
- **Pagos:** Certificación PCI DSS para procesamiento de tarjetas
- **Autenticación:** Contraseñas hasheadas con salt
- **Sesiones:** Tokens JWT con expiración

### 3.4 Usabilidad
- **Interfaz responsiva:** Compatible con móviles, tablets y desktop
- **Navegación intuitiva:** Máximo 3 clics para completar una reserva
- **Accesibilidad:** Cumplimiento con estándares WCAG 2.1 AA
- **Idioma:** Español como idioma principal

### 3.5 Disponibilidad
- **Uptime:** 99.5% mínimo (43.8 horas de downtime anual máximo)
- **Backup:** Respaldos diarios automáticos
- **Recuperación:** RTO < 4 horas, RPO < 1 hora

### 3.6 Compatibilidad
- **Navegadores:** Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **Dispositivos móviles:** iOS 13+, Android 9+
- **Resoluciones:** Desde 320px (móvil) hasta 1920px (desktop)

---

## 4. Arquitectura Técnica Sugerida

### 4.1 Stack Tecnológico Recomendado

**Frontend:**
- **Framework:** React.js 18+ con TypeScript
- **Styling:** Tailwind CSS o Material-UI
- **Estado:** Redux Toolkit o Zustand
- **Formularios:** React Hook Form
- **Calendario:** React Big Calendar o FullCalendar

**Backend:**
- **Runtime:** Node.js 18+ con Express.js
- **Base de datos:** PostgreSQL 14+
- **ORM:** Prisma o TypeORM
- **Autenticación:** JWT + bcrypt
- **Pagos:** Stripe o PayPal SDK

**Infraestructura:**
- **Hosting:** AWS/Digital Ocean/Vercel
- **CDN:** CloudFlare para assets estáticos
- **Email:** SendGrid o AWS SES
- **Monitoreo:** Sentry para errores

### 4.2 Estructura de Base de Datos

```sql
-- Usuarios
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  full_name VARCHAR(255) NOT NULL,
  email VARCHAR(255) UNIQUE NOT NULL,
  phone VARCHAR(20) NOT NULL,
  document_id VARCHAR(50) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  email_verified BOOLEAN DEFAULT FALSE,
  role ENUM('client', 'admin') DEFAULT 'client',
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Canchas
CREATE TABLE courts (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  description TEXT,
  status ENUM('active', 'maintenance', 'inactive') DEFAULT 'active',
  hourly_rate DECIMAL(10,2) NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Reservas
CREATE TABLE reservations (
  id SERIAL PRIMARY KEY,
  user_id INTEGER REFERENCES users(id),
  court_id INTEGER REFERENCES courts(id),
  reservation_date DATE NOT NULL,
  start_time TIME NOT NULL,
  duration_hours DECIMAL(2,1) NOT NULL CHECK (duration_hours IN (1.0, 1.5, 2.0)),
  total_amount DECIMAL(10,2) NOT NULL,
  paid_amount DECIMAL(10,2) NOT NULL,
  payment_status ENUM('pending', 'partial', 'completed', 'refunded') DEFAULT 'pending',
  status ENUM('active', 'cancelled', 'completed', 'no_show') DEFAULT 'active',
  notes TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Pagos
CREATE TABLE payments (
  id SERIAL PRIMARY KEY,
  reservation_id INTEGER REFERENCES reservations(id),
  amount DECIMAL(10,2) NOT NULL,
  payment_method ENUM('online', 'cash', 'card') NOT NULL,
  payment_provider VARCHAR(50), -- stripe, paypal, etc.
  provider_transaction_id VARCHAR(255),
  status ENUM('pending', 'completed', 'failed', 'refunded') DEFAULT 'pending',
  processed_at TIMESTAMP,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Configuración del sistema
CREATE TABLE system_settings (
  id SERIAL PRIMARY KEY,
  key VARCHAR(100) UNIQUE NOT NULL,
  value TEXT NOT NULL,
  description TEXT,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### 4.3 Endpoints de API Principales

**Autenticación:**
```
POST /api/auth/register
POST /api/auth/login
POST /api/auth/logout
POST /api/auth/forgot-password
POST /api/auth/reset-password
GET  /api/auth/verify-email/:token
```

**Usuarios:**
```
GET    /api/users/profile
PUT    /api/users/profile
GET    /api/users/reservations
DELETE /api/users/:id (admin)
```

**Canchas:**
```
GET /api/courts
GET /api/courts/:id
GET /api/courts/availability?date=YYYY-MM-DD
PUT /api/courts/:id (admin)
```

**Reservas:**
```
POST   /api/reservations
GET    /api/reservations/:id
PUT    /api/reservations/:id/cancel
GET    /api/reservations (admin)
PUT    /api/reservations/:id/status (admin)
```

**Pagos:**
```
POST /api/payments/create-intent
POST /api/payments/confirm
GET  /api/payments/:id/status
POST /api/payments/webhook (stripe/paypal)
```

### 4.4 Integración de Pagos

**Flujo de Pago Parcial (50%):**
1. Cliente selecciona "Pago Parcial"
2. Se crea PaymentIntent por el 50% del total
3. Cliente completa el pago en línea
4. Reserva se confirma con status "partial"
5. Sistema registra saldo pendiente

**Flujo de Pago Completo (100%):**
1. Cliente selecciona "Pago Completo"
2. Se crea PaymentIntent por el 100% del total
3. Cliente completa el pago en línea
4. Reserva se confirma con status "completed"

---

## 5. Manejo de Errores y Excepciones

### 5.1 Códigos de Error Estándar

```javascript
const ERROR_CODES = {
  // Autenticación (1000-1099)
  INVALID_CREDENTIALS: { code: 1001, message: "Email o contraseña incorrectos" },
  EMAIL_NOT_VERIFIED: { code: 1002, message: "Por favor verifica tu email" },
  ACCOUNT_LOCKED: { code: 1003, message: "Cuenta bloqueada temporalmente" },
  
  // Reservas (2000-2099)
  COURT_NOT_AVAILABLE: { code: 2001, message: "La cancha no está disponible en el horario seleccionado" },
  INVALID_TIME_SLOT: { code: 2002, message: "Horario fuera del rango permitido (8AM-10PM)" },
  RESERVATION_NOT_FOUND: { code: 2003, message: "Reserva no encontrada" },
  CANNOT_CANCEL: { code: 2004, message: "No se puede cancelar con menos de 2 horas de anticipación" },
  
  // Pagos (3000-3099)
  PAYMENT_FAILED: { code: 3001, message: "Error al procesar el pago" },
  INSUFFICIENT_FUNDS: { code: 3002, message: "Fondos insuficientes" },
  PAYMENT_TIMEOUT: { code: 3003, message: "Tiempo de pago agotado" },
  
  // Sistema (4000-4099)
  SERVER_ERROR: { code: 4001, message: "Error interno del servidor" },
  MAINTENANCE_MODE: { code: 4002, message: "Sistema en mantenimiento" },
  RATE_LIMIT_EXCEEDED: { code: 4003, message: "Demasiadas solicitudes" }
};
```

### 5.2 Manejo de Errores por Componente

**Frontend (React):**
```javascript
// Error Boundary para errores de React
class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, errorInfo) {
    // Log error to monitoring service
    console.error('Error caught by boundary:', error, errorInfo);
  }

  render() {
    if (this.state.hasError) {
      return <ErrorFallback />;
    }
    return this.props.children;
  }
}
```

**Backend (Express):**
```javascript
// Middleware global de manejo de errores
app.use((err, req, res, next) => {
  console.error(err.stack);
  
  if (err.code && ERROR_CODES[err.code]) {
    return res.status(400).json({
      success: false,
      error: ERROR_CODES[err.code]
    });
  }
  
  res.status(500).json({
    success: false,
    error: ERROR_CODES.SERVER_ERROR
  });
});
```

### 5.3 Estrategias de Recuperación

**Fallos de Pago:**
- Reintentar automáticamente hasta 3 veces
- Mostrar métodos de pago alternativos
- Guardar reserva temporalmente (15 minutos)

**Fallos de Conectividad:**
- Modo offline para consultar reservas existentes
- Queue de operaciones para sincronizar cuando se restaure conexión
- Notificación clara del estado de conexión

**Fallos de Base de Datos:**
- Connection pooling con retry automático
- Fallback a cache de Redis para consultas
- Modo de solo lectura si hay problemas de escritura

---

## 6. Plan de Pruebas (Test Plan)

### 6.1 Pruebas Unitarias

**Módulo de Autenticación:**
```javascript
describe('Authentication Service', () => {
  test('should hash password correctly', () => {
    const password = 'testPassword123';
    const hashedPassword = authService.hashPassword(password);
    expect(bcrypt.compareSync(password, hashedPassword)).toBe(true);
  });

  test('should generate valid JWT token', () => {
    const userId = 123;
    const token = authService.generateToken(userId);
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    expect(decoded.userId).toBe(userId);
  });
});
```

**Módulo de Reservas:**
```javascript
describe('Reservation Service', () => {
  test('should check court availability correctly', async () => {
    const courtId = 1;
    const date = '2025-09-27';
    const startTime = '14:00';
    const duration = 1.5;
    
    const isAvailable = await reservationService.checkAvailability(
      courtId, date, startTime, duration
    );
    
    expect(typeof isAvailable).toBe('boolean');
  });

  test('should calculate price correctly', () => {
    const duration = 1.5;
    const hourlyRate = 20;
    const totalPrice = reservationService.calculatePrice(duration, hourlyRate);
    expect(totalPrice).toBe(30);
  });
});
```

### 6.2 Pruebas de Integración

**Flujo Completo de Reserva:**
```javascript
describe('Complete Reservation Flow', () => {
  test('should complete full reservation with payment', async () => {
    // 1. Registrar usuario
    const user = await testUtils.createTestUser();
    
    // 2. Login
    const token = await testUtils.loginUser(user.email);
    
    // 3. Seleccionar cancha disponible
    const availableSlot = await testUtils.findAvailableSlot();
    
    // 4. Crear reserva
    const reservation = await testUtils.createReservation(availableSlot, token);
    
    // 5. Procesar pago
    const payment = await testUtils.processPayment(reservation.id, 'full');
    
    // 6. Verificar confirmación
    expect(reservation.status).toBe('active');
    expect(payment.status).toBe('completed');
  });
});
```

### 6.3 Pruebas de Rendimiento

**Carga de Usuarios Concurrentes:**
```javascript
// Usando Artillery.js
module.exports = {
  config: {
    target: 'http://localhost:3000',
    phases: [
      { duration: 300, arrivalRate: 10 }, // 10 usuarios/segundo por 5 minutos
      { duration: 300, arrivalRate: 20 }, // Escalar a 20 usuarios/segundo
    ]
  },
  scenarios: [
    {
      name: 'Complete reservation flow',
      weight: 70,
      flow: [
        { post: { url: '/api/auth/login', json: '{{ userCredentials }}' }},
        { get: { url: '/api/courts/availability?date=2025-09-27' }},
        { post: { url: '/api/reservations', json: '{{ reservationData }}' }},
        { post: { url: '/api/payments/create-intent', json: '{{ paymentData }}' }}
      ]
    }
  ]
};
```

### 6.4 Criterios de Aceptación por Funcionalidad

**Registro de Usuario:**
- ✅ Todos los campos obligatorios validados
- ✅ Email único en el sistema
- ✅ Documento de identidad único
- ✅ Contraseña cumple requisitos de seguridad
- ✅ Email de verificación enviado

**Proceso de Reserva:**
- ✅ Solo horarios disponibles se pueden seleccionar
- ✅ Precio calculado correctamente según duración
- ✅ Reserva no se confirma sin pago exitoso
- ✅ Confirmación enviada por email
- ✅ Calendario se actualiza inmediatamente

**Procesamiento de Pagos:**
- ✅ Integración con pasarela funciona correctamente
- ✅ Manejo adecuado de pagos fallidos
- ✅ Reembolsos procesados correctamente
- ✅ Webhooks de pago manejados apropiadamente

---

## 7. Notas de Despliegue y Dependencias

### 7.1 Requisitos de Entorno

**Servidor de Desarrollo:**
- Node.js 18.0+
- PostgreSQL 14+
- Redis 6+ (para cache y sesiones)
- Git
- NPM o Yarn

**Servidor de Producción:**
- **CPU:** 2 cores mínimo (4 cores recomendado)
- **RAM:** 4GB mínimo (8GB recomendado)
- **Almacenamiento:** 50GB SSD mínimo
- **Ancho de banda:** 100Mbps
- **OS:** Ubuntu 20.04 LTS o CentOS 8+

### 7.2 Variables de Entorno Requeridas

```bash
# Base de datos
DATABASE_URL=postgresql://user:password@localhost:5432/futbolito_reservas
REDIS_URL=redis://localhost:6379

# Autenticación
JWT_SECRET=your-super-secret-jwt-key
JWT_EXPIRATION=24h

# Email
SENDGRID_API_KEY=your-sendgrid-api-key
FROM_EMAIL=noreply@tufutbolito.com

# Pagos
STRIPE_SECRET_KEY=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...
STRIPE_PUBLISHABLE_KEY=pk_test_...

# Configuración de aplicación
NODE_ENV=production
PORT=3000
FRONTEND_URL=https://www.tufutbolito.com
ADMIN_EMAIL=admin@tufutbolito.com
```

### 7.3 Pasos de Despliegue Inicial

**1. Preparación del Servidor:**
```bash
# Actualizar sistema
sudo apt update && sudo apt upgrade -y

# Instalar Node.js
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs

# Instalar PostgreSQL
sudo apt install postgresql postgresql-contrib

# Instalar Redis
sudo apt install redis-server

# Instalar PM2 para gestión de procesos
sudo npm install -g pm2
```

**2. Configuración de Base de Datos:**
```bash
# Crear usuario y base de datos
sudo -u postgres psql
CREATE USER futbolito_user WITH PASSWORD 'secure_password';
CREATE DATABASE futbolito_reservas OWNER futbolito_user;
GRANT ALL PRIVILEGES ON DATABASE futbolito_reservas TO futbolito_user;
\q

# Ejecutar migraciones
npm run migrate
npm run seed
```

**3. Despliegue de Aplicación:**
```bash
# Clonar repositorio
git clone https://github.com/tu-repo/futbolito-reservas.git
cd futbolito-reservas

# Instalar dependencias
npm install

# Construir aplicación
npm run build

# Configurar PM2
pm2 start ecosystem.config.js
pm2 save
pm2 startup
```

### 7.4 Configuración de Nginx (Proxy Reverso)

```nginx
server {
    listen 80;
    server_name www.tufutbolito.com tufutbolito.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name www.tufutbolito.com tufutbolito.com;

    ssl_certificate /path/to/ssl/certificate.crt;
    ssl_certificate_key /path/to/ssl/private.key;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }
}
```

### 7.5 Configuración de Backup

```bash
#!/bin/bash
# Script de backup diario
DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_DIR="/var/backups/futbolito"

# Crear directorio si no existe
mkdir -p $BACKUP_DIR

# Backup de base de datos
pg_dump -h localhost -U futbolito_user futbolito_reservas > $BACKUP_DIR/db_backup_$DATE.sql

# Backup de archivos de aplicación
tar -czf $BACKUP_DIR/app_backup_$DATE.tar.gz /var/www/futbolito-reservas

# Limpiar backups antiguos (mantener últimos 7 días)
find $BACKUP_DIR -name "*.sql" -mtime +7 -delete
find $BACKUP_DIR -name "*.tar.gz" -mtime +7 -delete
```

### 7.6 Monitoreo y Logs

**Configuración de PM2 para logs:**
```json
{
  "apps": [{
    "name": "futbolito-api",
    "script": "./dist/index.js",
    "instances": "max",
    "exec_mode": "cluster",
    "log_file": "/var/log/futbolito/combined.log",
    "out_file": "/var/log/futbolito/out.log",
    "error_file": "/var/log/futbolito/error.log",
    "log_date_format": "YYYY-MM-DD HH:mm:ss Z"
  }]
}
```

**Health Check Endpoint:**
```javascript
// GET /api/health
app.get('/api/health', async (req, res) => {
  try {
    // Verificar conexión a base de datos
    await db.query('SELECT 1');
    
    // Verificar Redis
    await redis.ping();
    
    res.json({
      status: 'healthy',
      timestamp: new Date().toISOString(),
      uptime: process.uptime(),
      version: process.env.npm_package_version
    });
  } catch (error) {
    res.status(503).json({
      status: 'unhealthy',
      error: error.message
    });
  }
});
```

---

## Referencias Cruzadas y Documentación Auxiliar

- **Diagrama de Flujo Principal:** `[specifications/diagramas/flujo-principal.png]`
- **Mockups de UI:** `[specifications/mockups/]`
- **Diagrama de Base de Datos:** `[specifications/diagramas/database-schema.png]`
- **Configuración de Stripe:** `[specifications/integraciones/stripe-setup.md]`
- **Guía de Testing:** `[specifications/testing/test-guidelines.md]`

---

**Documento preparado para implementación inmediata**  
**Próximos pasos:** Iniciar setup de entorno de desarrollo según sección 7