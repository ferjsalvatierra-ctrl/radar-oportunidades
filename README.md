# Radar de oportunidades

Herramienta personal para encontrar y seguir **consultorías internacionales, empleos, convocatorias de investigación y conferencias** en IA, educación y políticas digitales, puntuadas según el perfil de Fernando Salvatierra.

- **Versión en vivo:** https://claude.ai/artifact/UGa2B6YHrpLTqCG2L5kfLi (privada; necesita sesión en claude.ai)
- **Automatización:** dos tareas programadas de Claude
  - Escaneo web: lunes, miércoles y viernes 7:13 (hora de Buenos Aires), en la nube.
  - Escaneo Chrome: martes y jueves 20:41, en la computadora de Fernando, con sus sesiones de LinkedIn, Devex e Impactpool.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | La página: radar con filtros, seguimiento por estado, análisis de TdR con Claude, fuentes y perfil. Usa las capacidades `db`, `user` y `sample` del runtime de artifacts de Claude. |
| `sources.json` | Catálogo de 52 fuentes (ONU, bancos de desarrollo, agregadores, fondos de investigación, conferencias). `via: "web"` o `"chrome"`. Se carga en `config/sources`. |
| `profile.json` | Perfil, palabras clave, exclusiones, tarifas y rúbrica de puntaje. Se carga en `config/profile`. |
| `SCANNER.md` | Instrucciones de los escaneos automáticos. |

## Lógica de puntaje (0–100)

| Criterio | Máx. | Puntúa alto cuando… |
|---|---|---|
| Tema | 35 | IA, educación digital, políticas digitales, EdTech; desarrollo de plataformas (Moodle, simuladores) |
| Nivel | 20 | Senior, experto principal, P-4/P-5, consultoría nivel C-D o Level 3 |
| Región | 15 | América Latina y el Caribe, español o remoto |
| Modalidad | 10 | Por producto, LTA o remota |
| Pago | 10 | ≥ USD 650/día o P-4+ (mínimo USD 450/día) |
| Plazo | 10 | Más de 14 días para el cierre |

Prioridad: **Alta** ≥ 75 · **Media** 55–74 · **Baja** < 55. Alertas automáticas: posible incompatibilidad con IIPE/UNESCO, idiomas o doctorado exigidos, cierre en menos de 7 días.

## Modelo de datos (db del artifact)

- `config/sources` · `config/profile` · `meta/scan`
- `opps/<id>`: `title, org, cat, url, source, location, modality, rate, lang, deadline, score, breakdown, flags, reasons, summary, foundAt, addedBy`
- `data/users/<id>/tracker`: estado privado de cada oportunidad (nuevo, me interesa, preparando, enviada, entrevista, ganada, descartada)

## Publicar cambios

Editá `index.html` y pedile a Claude que republique el artifact `dcd33ff4-03eb-46dd-b96b-3e84cb1a4a67`. Para cambiar fuentes o palabras clave no hace falta tocar código: se editan desde las pestañas **Fuentes** y **Perfil y lógica**.
