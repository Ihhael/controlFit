# 01b · Estado del arte (SOTA) de mi proyecto

## 1. Problema y preguntas de búsqueda (CE 1c)

### 1.1. Problema en una frase

La persona que acude al gimnasio a entrenar con pesas necesita un medio para **registrar sus sesiones** (ejercicios, series, repeticiones y cargas) y para **consultar su evolución**. Hoy esta tarea se deja en papel o bolígrafo, lo que dificulta el control de la carga y el seguimiento de la constancia.

### 1.2. Preguntas de búsqueda

| #    | Pregunta                                                     | Dónde busqué                                                 | Fecha   |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------- |
| P1   | ¿Qué soluciones existen que resuelvan, en total o en parte, el control de las sesiones de entrenamiento? | Buscadores web, tiendas de aplicaciones, repositorios de código | 2026-11 |
| P2   | ¿Cómo generan ingresos los actores del sector del fitness digital? | Webs oficiales, informes de mercado                          | 2026-11 |
| P3   | ¿Qué tecnologías, herramientas y modelos de negocio usan las soluciones del sector? | Documentación técnica y webs oficiales                       | 2026-11 |
| P4   | ¿Qué hueco queda para una solución especializada en el control de fuerza? | Análisis comparativo de soluciones                           | 2026-11 |

## 2. Soluciones existentes (CE 1a, 1c, 2a)

| Solución               | Para quién                 | Qué hace                                                     | Modelo de precio        | Enlace y fecha de acceso      |
| ---------------------- | -------------------------- | ------------------------------------------------------------ | ----------------------- | ----------------------------- |
| **Gympass**            | Gimnasios y entrenadores   | Plataforma **B2B2C**: gestiona clientes, rutinas y control de entrenamiento | Suscripción empresarial | `gympass.com` — 2026-11       |
| **ClassPass**          | Deportistas                | **Marketplace B2C** de clases y entrenamientos               | Freemium / suscripción  | `classpass.com` — 2026-11     |
| **Fitbod**             | Deportistas individuales   | **App B2C** personalizada de entrenamiento                   | Suscripción             | `fitbod.com` — 2026-11        |
| **TrainingPeaks**      | Deportistas de resistencia | Registro y planificación de entrenamiento                    | Freemium                | `trainingpeaks.com` — 2026-11 |
| **Zebris**             | Deportistas de fuerza      | **Hardware de conteo + app** de registro                     | Licencia                | `zebris.com` — 2026-11        |
| **Nike Training Club** | Deportistas B2C            | Entrenamientos guiados                                       | Gratuita                | `nike.com` — 2026-11          |

*Figura: comparativa de las soluciones estudiadas.*

## 3. Modelos de negocio (CE 1d, 1e)

| Patrón               | Soluciones que lo usan                       | Ventaja                           | Riesgo                       |
| -------------------- | -------------------------------------------- | --------------------------------- | ---------------------------- |
| Suscripción          | Gympass, Fitbod                              | Ingresos recurrentes, predicibles | Dificultad de diferenciación |
| Freemium             | ClassPass, TrainingPeaks, Nike Training Club | Adquisición masiva                | Coste de servido gratuito    |
| Gratuito / contenido | Nike Training Club                           | Alcance amplio                    | No monetiza la base activa   |

Sobre los **2-3 casos** analizados (Gympass, Fitbod y Nike Training Club) y el modelo que seguiría **ControlFit**.

## 4. Herramientas y tecnologías (CE 2a, 2b)

| Decisión             | Opción                            | Madurez | Licencia   | Coste  | Curva de aprendizaje | Encaje con el ciclo   | Elegida |
| -------------------- | --------------------------------- | ------- | ---------- | ------ | -------------------- | --------------------- | ------- |
| Lenguaje y framework | Java 21 + Spring Boot             | Alta    | Apache 2.0 | Gratis | Media                | Sí (ciclo del alumno) | **Sí**  |
| Base de datos        | SQL (MySQL / SQLite)              | Alta    | —          | Gratis | Baja                 | Sí                    | **Sí**  |
| Despliegue           | Docker                            | Alta    | —          | Gratis | Media                | Sí                    | **Sí**  |
| Autenticación        | Sesión servidor (Spring Security) | Alta    | —          | Gratis | Media                | Sí                    | **Sí**  |

## 5. Hueco y diferenciación (CE 1e)

¿Qué no cubren las soluciones del apartado 2 y qué aporta ControlFit:

- Las soluciones existentes no ofrecen de forma integrada el **control de sesiones de fuerza** con **series, repeticiones y cargas** para el deportista individual.
- ControlFit cubre ese hueco con una **aplicación web** propia, centrada en crear rutinas, registrar ejercicios, controlar series y repeticiones, anotar pesos y consultar la evolución.

## 6. Decisiones derivadas (CE 1e, 1f, 2b)

- **Tipo de proyecto elegido** (enlaza con el apartado 3 de [`01-analisis.md`](01-analisis.md)): la aplicación web ControlFit.
- **Requisitos que salen del estudio** (con su ID del apartado 4 de `01-analisis.md`): RF-03 (registro de sesión con series, repeticiones y carga).
- **Decisiones técnicas** (enlace a cada archivo de `decisiones/`): pendiente (ficheros por crear en la fase de diseño).

## 7. Fuentes y calidad (CE 2a)

| #    | Fuente (enlace)             | Tipo               | Fecha de acceso | Fiabilidad (alta / media / baja) y por qué |
| ---- | --------------------------- | ------------------ | --------------- | ------------------------------------------ |
| F1   | `https://www.gympass.com`   | Empresa del sector | 2026-11         | Alta (web oficial).                        |
| F2   | `https://www.classpass.com` | Empresa del sector | 2026-11         | Alta (web oficial).                        |

## 8. Límites

- No se han podido comprobar en esta fase los **precios exactos** de las soluciones ni todos los **datos de acceso** a las fuentes indicadas.
- Los datos de mercado citados como estimaciones deberán contrastarse con las fuentes originales antes de su uso en la memoria.

---

## Criterios de evaluación que alimenta este documento (texto literal)

- **1a)** Se han clasificado las empresas del sector por sus características organizativas y el tipo de producto o servicio que ofrecen.
- **1c)** Se han identificado las necesidades más demandadas a las empresas.
- **1d)** Se han valorado las oportunidades de negocio previsibles en el sector.
- **1e)** Se ha identificado el tipo de proyecto requerido para dar respuesta a las demandas previstas.
- **1f)** Se han determinado las características específicas requeridas al proyecto.
- **2a)** Se ha recopilado información relativa a los aspectos que van a ser tratados en el proyecto.
- **2b)** Se ha realizado el estudio de viabilidad técnica del mismo.
