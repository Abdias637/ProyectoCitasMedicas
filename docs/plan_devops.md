# Plan DevOps del Proyecto Móvil

## 5) Configuración del repositorio y CI mínimo

- Se creó el repositorio **ProyectoCitasMedicas** en GitHub.
- Se agregó la siguiente **estructura base**:

```
/docs/                  # Documentación Plan DevOps y Comunicación
/app/                   # Código de la app móvil (Flutter)
/ci/                    # Scripts y workflows
/.github/workflows/     # Pipelines de CI/CD (GitHub Actions)
README.md               # Guía del proyecto
ISSUE_TEMPLATE.md       # Plantilla de issues
PULL_REQUEST_TEMPLATE.md# Plantilla de PRs
.gitignore              # Exclusiones de Git
```

- Se configuró un **workflow CI mínimo** con GitHub Actions:
  - **push a `develop`** → ejecuta build y lint.
  - **pull_request hacia `main`** → ejecuta build y tests.
- Se añadieron plantillas de **issues** y **pull requests** para estandarizar la colaboración.
- Se configuraron ramas principales:
  - `main`: estable y protegida.
  - `develop`: integración.
  - `feature/*` y `hotfix/*` para nuevas funciones y correcciones urgentes.

---

## 6) Plan DevOps del Proyecto Móvil

- **CI/CD**: se validan los cambios en cada PR con compilación y pruebas. Los merges a `main` solo ocurren si el pipeline pasa.
- **Estrategia de pruebas**:
  - *Unitarias*: validación de datos.
  - *Widget/UI*: navegación y pantallas.
  - *Integración*: flujo login → agendar cita.
  - Criterio de salida: 0 errores críticos y cobertura ≥70%.
- **Estrategia de despliegue**:
  - Testing: Firebase App Distribution / TestFlight.
  - Producción: Google Play Store / App Store.
  - *Feature flags* para liberar funciones gradualmente.
- **Monitoreo y métricas**:
  - Crashlytics / Sentry → errores críticos.
  - Firebase Performance → tiempos de carga.
  - KPIs: sesiones activas, citas agendadas, tasa de cancelaciones.
- **Riesgos y mitigación**:
  - Fallas CI/CD → rollback automático.
  - Credenciales → rotación con GitHub Secrets.
  - Bajo engagement → notificaciones push y encuestas.
  - Errores en prod. → logs centralizados + hotfix branch.
  - Sobrecarga de servidor → monitoreo de SLIs y escalado.
- **Runbook corto**:
  - Build roto → `flutter clean`, revisar dependencias.
  - Credenciales expiran → regenerar tokens y actualizar Secrets.
  - Cuota API excedida → cambiar key temporal, avisar al PO.

---

## 7) Selección de herramienta de comunicación

- **Candidatas evaluadas**: Slack, Teams, Discord, Google Chat.
- **Matriz comparativa** → Teams resultó con mayor puntaje (26/30).
- **Dictamen**:
  - Se eligió **Microsoft Teams** por integración con calendario, seguridad, y mayor historial.
  - Riesgos: consumo de recursos y límites en plan gratuito → mitigación: canales claros y limpieza de archivos.
- **Configuración mínima**:
  - Canales: `#anuncios`, `#dev`, `#qa`, `#ops`, `#dudas`, `#random`.
  - Normas: respuesta ≤12h, uso de hilos, daily de 15 min, menciones solo en bloqueos.
  - Integraciones: CI notifica en `#dev`, tableros en `#anuncios`.

---

## 8) Evidencias y cierre

- **README** actualizado con:
  - Descripción del proyecto.
  - Status badge de GitHub Actions.
  - Estructura del repositorio.
  - Instrucciones de build (`flutter pub get && flutter run`).
- **Demo breve** (3–5 min) preparada:
  - Explicar ciclo DevOps.
  - Mostrar board de Sprint 0 en Trello/GitHub Projects.
  - Mostrar Teams con canales creados.
