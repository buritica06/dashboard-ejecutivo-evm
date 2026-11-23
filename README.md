# Dashboard Ejecutivo EVM · Mantilla Gil

Suite de tableros web estáticos para seguimiento y control de proyectos bajo la metodología de **Valor Ganado (EVM / PMBOK®)** y analítica de portafolio.

## Contenido del Proyecto

| Archivo | Descripción |
| :--- | :--- |
| `index.html` | Portal de entrada corporativo con acceso directo a ambos dashboards. |
| `dashboard_ejecutivo_evm.html` | Dashboard ejecutivo EVM (finanzas, cronograma ganado, recursos, Gantt y matriz de riesgos) con Apache ECharts 5.5.0. |
| `dashboard_project_management.html` | Tablero analítico multipágina (*Overview*, *Performance* y *Tracking*) en HTML/CSS/JS y SVG puro sin dependencias externas. |
| `logo_mantilla_gil.png` | Logotipo corporativo utilizado en el portal de entrada. |

## Arquitectura

- **Tipo:** Sitio web estático (*zero-build*, 100% cliente).
- **Tecnologías:** HTML5, CSS3 (CSS Grid responsivo), JavaScript ES6+, SVG nativo.
- **Dependencias externas (CDN):**
  - Apache ECharts `5.5.0` (`cdnjs.cloudflare.com`) — utilizado en `dashboard_ejecutivo_evm.html`.
  - Google Fonts (`Inter` y `Source Serif 4`).
- **Variables de entorno:** Ninguna requerida.

## Ejecución Local

No requiere instalación ni compilación. Puede abrir `index.html` directamente o levantar un servidor local:

```bash
# Con Python 3
python -m http.server 8080

# O con Node.js
npx serve .
```

Luego abra `http://localhost:8080` en su navegador.

## Despliegue Automático (CI/CD)

El repositorio incluye el workflow [`.github/workflows/deploy-pages.yml`](.github/workflows/deploy-pages.yml) que, en cada `push` a `main` o ejecución manual (`workflow_dispatch`):

1. Valida la integridad de los archivos requeridos y la ausencia de archivos locales sensibles.
2. Empaqueta únicamente los activos públicos estáticos en `_site/`.
3. Publica automáticamente el sitio en **GitHub Pages** mediante `actions/deploy-pages`.

## Seguridad

- No se almacenan credenciales, tokens ni secretos en el repositorio.
- Los archivos locales de configuración de herramientas (`.claude/`, `.env`, etc.) están excluidos en `.gitignore`.
