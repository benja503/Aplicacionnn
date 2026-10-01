# PLATO ECONÓMICO

> Ayuda a estudiantes y familias con presupuesto ajustado a comer de forma balanceada y variada aprovechando los ingredientes disponibles en casa sin desperdiciar comida ni dinero.

---

## 1. Probala ahora
- **App publicada:** [https://morenojerson.github.io/plato-economico](https://morenojerson.github.io/plato-economico)
- **Código QR:**  
  ![Código QR de acceso a Plato Económico](evidencias/qr.png)
- **Usuario de prueba:** No requiere registro ni contraseña; funciona de forma instantánea y offline en cualquier navegador o teléfono celular.

---

## 2. Capturas
| Inicio y Despensa | En uso (Filtro y Menú) | Con la IA trabajando (Chef IA) |
|---|---|---|
| ![Pantalla de inicio](evidencias/E3-celular.png) | ![Filtro de recetas y menú](evidencias/E1-despues.png) | ![Chef IA generando JSON](evidencias/E5-app.png) |

---

## 3. Qué hace
- **Gestión visual de despensa y presupuesto:** Permite ingresar ingredientes disponibles en el hogar (uno a uno o mediante chips rápidos) y fijar un presupuesto máximo por porción en dólares estadounidenses (USD).
- **Filtrado inteligente de recetas económicas:** Muestra automáticamente platos cuyo costo estimado por porción sea igual o menor al presupuesto, calculando qué ingredientes ya tienes en casa y cuáles te faltan por comprar.
- **Planificador de Menú Semanal:** Permite guardar y organizar recetas en favoritos con persistencia local (`localStorage`), calculando el costo total consolidado y generando una lista de compras automática.
- **Asistente Chef IA con salida estructurada en JSON:** Analiza en tiempo real los ingredientes disponibles y el presupuesto mediante la API de Gemini (o su motor gastronómico local de respaldo), entregando una optimización nutricional estructurada en formato JSON estricto con tips de ahorro y nutrición express.

---

## 4. Cómo correrlo en tu máquina
```bash
# 1. Clonar el repositorio
git clone https://github.com/morenojerson/plato-economico.git
cd plato-economico

# 2. Configurar variables (opcional, para usar la API de Google Gemini en remoto)
cp .env.example .env
# Editar .env y colocar tu GEMINI_API_KEY si deseas llamadas directas a la nube

# 3. Iniciar un servidor web local liviano (o simplemente abrir index.html en tu navegador)
python3 -m http.server 8000
# Abrir http://localhost:8000 en el navegador de tu computadora o celular
```

---

## 5. Tecnologías
- **Lenguajes:** HTML5 Semántico, CSS3 moderno (Variables CSS, Flexbox, Grid, Animaciones y Microinteracciones) y JavaScript Vanilla (ES6+).
- **Persistencia de datos:** Web Storage API (`localStorage`) para despensa, presupuesto, menú semanal y planes de IA del usuario.
- **Inteligencia Artificial:** Google Gemini API (`gemini-3.5-flash`) con salida estructurada `application/json` mediante REST y motor heurístico gastronómico determinista como fallback offline.
- **Plataforma Android:** Proyecto base compatible con Android WebView / Jetpack Compose para empaquetado nativo (APK).

---

## 6. La escalera de mejoras
| Peldaño | Qué cambió | Commit | Evidencia |
|---|---|---|---|
| **P0** | Versión inicial en un solo archivo con búsqueda básica por presupuesto e ingredientes | `7f4a1b0` | `evidencias/E0-inicial.png` |
| **M1** | Agregado de ingredientes uno a uno, chips interactivos, cálculo de faltantes y costos por plato | `b2c9d31` | `evidencias/E1-antes.png` / `evidencias/E1-despues.png` |
| **M2** | Persistencia automática en `localStorage`, sección de "Menú Semanal" y botón "Limpiar Despensa" | `e4f5a62` | `evidencias/E2-antes.png` / `evidencias/E2-despues.png` |
| **M3** | Rediseño visual Mobile-First gastronómico, segmented tabs, empty states ilustrados y transiciones | `c8d1e23` | `evidencias/E3-celular.png` / `evidencias/E3-vacio.png` |
| **M4** | Sanitización de texto, prevención de duplicados, validación estricta de presupuesto y toast alerts | `9a3b7c4` | `evidencias/E4-error.png` |
| **M5** | Integración del **Chef IA** con salida estricta en JSON (`menu_optimizado`, `ahorro_estimado`, `recetas_sugeridas`), loader de cocina animado y renderizado comercial | `d5e6f75` | `evidencias/E5-json.png` / `evidencias/E5-app.png` / `evidencias/E5-falla.png` |

---

## 7. Prueba con usuarios reales
| Quién | Qué intentó | Dónde se trabó | Lo que dijo, textual | ¿Corregido? |
|---|---|---|---|---|
| **Compañero de clase** (Estudiante foráneo) | Intentó ingresar centavos con coma ("1,50") y el presupuesto se reseteaba a cero. | En el input de presupuesto numérico del navegador. | «Le puse 1,50 para buscar algo barato y me decía que el presupuesto era inválido.» | **Sí, en M4:** Se añadió sanitización y reemplazo automático de coma por punto decimal y slider táctil. |
| **Adulto del centro** (Madre de familia) | Quería saber exactamente cuánto iba a gastar en la semana con las recetas que eligió. | Tuvo que sumar manualmente plato por plato porque solo veía precios individuales. | «Me gusta la idea, pero no sé cuánto dinero en total tengo que llevar al mercado.» | **Sí, en M5:** Se creó el banner financiero consolidado con costo total y lista de compras en «Mi Menú». |
| **Persona ajena al proyecto** (Joven no técnico) | Intentó usar la IA sin conexión a internet y temía que la aplicación se colgara. | Esperaba un error técnico o pantalla en blanco si no ponía una clave de API. | «Pensé que me iba a pedir registrarme o pagar una suscripción para que funcione el Chef.» | **Sí, en M5:** Se implementó motor dual: funciona al 100% offline con IA culinaria local o con API remota. |

---

## 8. Declaración de uso de inteligencia artificial
- **Herramienta y modelo:** Google AI Studio, Gemini 3.8 Flash y Claude 3.5 Sonnet asistiendo en el entorno de desarrollo.
- **Qué hizo la IA:** Generó propuestas de maquetación CSS, estructura del contrato JSON para el asistente gastronómico y la base de recetas económicas con tiempos de cocción promedio.
- **Qué hice yo:** Diseñé los requerimientos funcionales, refiné la paleta de colores y el sistema de diseño visual (verde salvia y terracota), establecí las reglas de negocio para el cálculo de costos por porción y verifiqué la usabilidad en pantallas móviles.
- **Qué verifiqué y cómo:** Comprobé manualmente que ninguna receta mostrada supere el presupuesto ingresado, validé que `localStorage` guardara los datos tras cerrar y reabrir el navegador, y testeé el comportamiento con despensa vacía y entradas con caracteres especiales.
- **Qué corregí de lo que la IA entregó:** La IA inicialmente sugirió ingredientes que no estaban disponibles en América Latina a precios bajos (ej. espárragos frescos); los reemplacé por insumos básicos accesibles (arroz, huevos, frijoles, pasta, tomate, cebolla, papas).

---

## 9. Tarjeta anti-alucinación
| Afirmación de la IA | Cómo la verifiqué | Resultado |
|---|---|---|
| «La API de Gemini puede invocarse desde el navegador cliente sin exponer la API Key de forma segura en producción.» | Revisión de las políticas de seguridad de Google Cloud y documentación oficial de API Keys de Gemini. | **Falso en producción:** Las claves en el cliente pueden ser inspeccionadas. Se aclaró que para uso personal/prototipo se guarda en `localStorage` o se utiliza el backend seguro con motor local. |
| «El evento `input` en `<input type="number">` captura correctamente comas decimales en todos los navegadores móviles.» | Pruebas directas en navegadores móviles Android (Chrome / WebView). | **Falso:** Los teclados numéricos en español ingresan `,` que a veces reporta valor vacío en `HTMLInputElement.value`. Se ajustó la validación con `step="0.25"` y fallback de texto. |
| «`localStorage` tiene capacidad ilimitada para almacenar recetas complejas.» | Documentación de especificación W3C Web Storage. | **Falso:** El límite estándar es de aproximadamente 5 MB. Se optimizó la estructura guardando solo los IDs de las recetas seleccionadas y no objetos duplicados. |

---

## 10. Limitaciones conocidas
- **Precios fijos promedio:** Los costos unitarios son estimaciones basadas en precios promedio regionales en USD; no están sincronizados en tiempo real con las APIs de supermercados locales.
- **Unidades de medida no personalizables:** El sistema calcula los faltantes por ingrediente entero o ración estándar, sin permitir por ahora especificar gramos exactos o mililitros.
- **Persistencia local exclusiva:** Si el usuario borra la caché/datos de su navegador o cambia de teléfono, la despensa y el menú guardado no se sincronizan en la nube.

---

## 11. Próximo paso
Si contara con una semana adicional de desarrollo:
1. **Escaneo de ticket de compra:** Implementar reconocimiento visual con la cámara usando Gemini Multimodal para cargar automáticamente los ingredientes comprados en el supermercado a la despensa.
2. **Exportar a WhatsApp / PDF:** Agregar un botón para compartir la lista de compras del menú semanal con formato limpio a través de mensajería instantánea.
3. **Conversor de monedas locales:** Permitir alternar entre USD, Pesos (ARS, MXN, COP) y otras divisas con tasas de conversión automáticas.

---

## 12. Autor
**Jerson Moreno** · 3.er año Desarrollo de Software · INDEL · octubre de 2026

---

## 13. Licencia
Este proyecto se encuentra bajo la Licencia **MIT**. Consulta el archivo `LICENSE` para más información.
