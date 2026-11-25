- # 01 · Análisis y documentación inicial (RA1)

  > Proyecto: **ControlFit** — aplicación web para crear rutinas, registrar ejercicios, controlar series y repeticiones, anotar pesos y consultar la evolución del entrenamiento.

  ## 1. Sector y empresas (CE 1a, 1b)

  ### 1.1. Clasificación del sector y empresas

  El sector analizado es el **fitness y la gestión del entrenamiento físico**, y más concretamente el subsector de las aplicaciones que ayudan a planificar, registrar y controlar las **sesiones de entrenamiento** (en especial de fuerza) y a consultar su evolución.

  Se han identificado **6 empresas** del sector, clasificadas por sus características organizativas y el tipo de producto o servicio que ofrecen:

  | N.º  | Empresa / producto | Producto o servicio                                          | Tipo de organización      |
  | ---- | ------------------ | ------------------------------------------------------------ | ------------------------- |
  | 1    | Gympass            | Plataforma **B2B2C**: el gimnasio/entrenador ofrece sus servicios de control a los deportistas | Corporación internacional |
  | 2    | ClassPass          | **Marketplace B2C** de clases y entrenamientos               | Startup                   |
  | 3    | Fitbod             | **App B2C** personalizada de entrenamiento                   | Startup                   |
  | 4    | TrainingPeaks      | **App B2C** de planificación y registro de entrenamiento deportivo | Startup                   |
  | 5    | Zebris             | **Hardware + app** de conteo y registro para el entrenamiento de fuerza | Startup                   |
  | 6    | Nike Training Club | **App B2C** de entrenamientos guiados                        | Corporación               |

  ### 1.2. Empresa tipo: Gympass

  Se detalla con el detalle solicitado la **empresa tipo** del sector: **Gympass**.

  ```mermaid
  flowchart TB
      CEO["Dirección / Dirección deportiva"]
      CEO --> COO["Dirección Operaciones"]
      CEO --> CDO["Dirección Desarrollo"]
      CEO --> CMO["Dirección Marketing"]
      CEO --> CVO["Dirección Ventas y Cuentas"]
      COO --> OPS["Operaciones y comunidad"]
      COO --> SUP["Atención al cliente y soporte"]
      CDO --> DEV["Equipo de desarrollo"]
      CMO --> ADS["Marketing digital y contenidos"]
      CVO --> SAL["Equipos comerciales"]
  ```

  | Departamento                    | Funciones                                                    |
  | ------------------------------- | ------------------------------------------------------------ |
  | Dirección / Dirección deportiva | Estrategia del producto, visión y objetivos del negocio.     |
  | Dirección Operaciones           | Gestión de comunidades, despliegue y coordinación de los servicios. |
  | Dirección Desarrollo            | Ingeniería de producto y evolución de la plataforma.         |
  | Dirección Marketing             | Captación, contenidos y comunicación.                        |
  | Dirección Ventas y Cuentas      | Negociación con gimnasios y entrenadores clientes.           |
  | Atención al cliente y soporte   | Soporte y atención de la comunidad.                          |

  ## 2. Necesidades y oportunidades (CE 1c, 1d)

  ### 2.1. Necesidades más demandadas

  Del análisis del sector se extraen las siguientes necesidades:

  | ID   | Necesidad                                                    | Prioridad  | Criterio de priorización                                     | Fuente                                |
  | ---- | ------------------------------------------------------------ | ---------- | ------------------------------------------------------------ | ------------------------------------- |
  | N-01 | Personas que acuden al gimnasio a entrenar con pesas y que **no disponen de un registro digital** de sus sesiones (ejercicios, series, repeticiones, cargas). | **Must**   | Alta frecuencia de uso y alto impacto sobre la constancia y el progreso. | Encuestas y observación en gimnasios. |
  | N-02 | Entrenadores y profesionales del fitness que **gestionan el control** de sus clientes (rutinas, sesiones, evolución). | **Should** | Impacto medio-alto, depende del modelo de negocio del entrenador. | Estudios del sector.                  |
  | N-03 | Personas que buscan **control y ajuste de carga** a lo largo del tiempo. | **Could**  | Impacto alto a medio plazo.                                  | Datos de mercado.                     |

  **Criterio de priorización** empleado: frecuencia de uso, impacto en el resultado buscado y esfuerzo previsto para cubrir la necesidad con una solución digital.

  ### 2.2. Oportunidades de negocio

  La necesidad priorizada (N-01) se considera la **oportunidad principal** del proyecto: la digitalización del control de las **sesiones de entrenamiento de fuerza**. El **dato cuantitativo** que la sustenta es el tamaño estimado del **mercado global de aplicaciones de fitness** (del orden de los **4.000 millones de euros**, estimación de informes sectoriales que deberá verificarse en sus fuentes), lo que avala la viabilidad de una solución especializada en este nicho.

  ## 3. Tipo de proyecto elegido (CE 1e)

  Se ha elegido como respuesta del proyecto la **aplicación web ControlFit**, que da respuesta a la necesidad de llevar el control de las sesiones de entrenamiento (rutinas, series, repeticiones, cargas) y de consultar la evolución.

  Frente a las alternativas:
  - **Libreta o hoja de cálculo**: no accesible, no acumula historial ni permite análisis de evolución.
  - **Aplicaciones comerciales existentes** (Gympass, Fitbod, TrainingPeaks, ClassPass, Zebris): orientadas a otros segmentos (clases, resistencia, entrenamiento guiado) o que no cubren el control individual de fuerza con series/reps/carga.

  ControlFit se posiciona en el **nicho del control personal de la sesión de fuerza**, frente a las soluciones del apartado 2 del [`01b-sota.md`](01b-sota.md).

  ## 4. Requisitos y restricciones (CE 1f)

  ### 4.1. Requisitos

  | ID      | Requisito                                                    | Tipo (funcional / no funcional / restricción) | Cómo se verifica                                             |
  | ------- | ------------------------------------------------------------ | --------------------------------------------- | ------------------------------------------------------------ |
  | RF-01   | El sistema permite **registrar un usuario** con credenciales de acceso y **autenticarlo** para acceder a su información. | funcional                                     | Prueba **P-01**: alta de usuario válida → cuenta activada; formato de correo inválido → rechazada; credenciales correctas → acceso concedido. |
  | RF-02   | El sistema permite **crear una rutina de ejercicio** para el usuario, con ejercicios y series/reps. | funcional                                     | Prueba **P-02**: creación de rutina → persistencia → listado para el usuario. |
  | RF-03   | El sistema permite **registrar una sesión de entrenamiento** con ejercicios, series, repeticiones y carga (peso). | funcional                                     | Prueba **P-03**: registro de sesión → actualización del historial. Fuera de la MVP (no es esencial en la primera versión mínima, según `00-documentoInicio.md`). |
  | RNF-01  | El sistema responde a las operaciones del dominio en **menos de 2 s**. | no funcional                                  | Prueba manual con cliente HTTP y medición del tiempo.        |
  | RNF-02  | Las contraseñas se almacenan con **hash** y las sesiones se gestionan por el servidor. | no funcional                                  | Verificación del valor almacenado en la base de datos (no legible en texto plano). |
  | RNF-03  | La interfaz permite completar las operaciones de creación de rutina y registro de sesión sin pasos redundantes. | no funcional                                  | Verificación con recorrido de usuario.                       |
  | RNF-04  | La interfaz es **accesible** (navegación por teclado, contraste, etiquetas). | no funcional                                  | Verificación con checklist de accesibilidad.                 |
  | REST-01 | El desarrollo se realizará con **Java 21 y Spring Boot**, sobre **base de datos SQL**, según lo previsto en el documento de inicio. | restricción                                   | Revisión del código y del entorno de desarrollo.             |
  | REST-02 | La **versión mínima funcional** debe estar disponible antes del **31-mar-2027**. | restricción                                   | Seguimiento con el tablero Kanban (GitHub Projects).         |

  ### 4.2. Matriz de trazabilidad

  | Objetivo                                | Requisito | Caso de uso | Pantalla o endpoint | Prueba o indicador |
  | --------------------------------------- | --------- | ----------- | ------------------- | ------------------ |
  | OBJ-01 · Gestionar rutinas de ejercicio | RF-02     | pendiente   | pendiente           | pendiente          |

  ## 5. Obligaciones fiscales, laborales y de prevención (CE 1g)

  - **Laborales y fiscales**: el proyecto se desarrolla como **proyecto personal** (sin empresa o centro que lo explote), por lo que no generan obligaciones laborales propias derivadas de una relación laboral. Si se financia a través de una ayuda, deberán cumplirse los requisitos de la convocatoria.
  - **Protección de datos**: los usuarios registrados aportan datos personales (aunque el proyecto se usará con datos ficticios), por lo que procede el cumplimiento del **RGPD** (consentimiento, finalidad, plazo, derechos de acceso/modificación/supresión).
  - **Prevención de riesgos**: trabajo en laboratorio informático con medidas de ergonomía y seguridad.

  ## 6. Ayudas y subvenciones (CE 1h)

  - **Ayuda identificada**: **Next for Industry** (CDTI), dentro de las ayudas de **Next Generation EU** para la digitalización de pymes y empresas. Requisitos y plazo de la convocatoria vigente deben confirmarse con el tutor.

  ## 7. Guion de trabajo (CE 1i)

  - **Fase 0 · Inicio** (6-nov-2026): repositorio, documentación inicial y primer PR aprobado.
  - **Fase 1 · Análisis** (6-nov a 26-nov-2026): entrega **H1** (análisis y documentación inicial).
  - **Fase 2 · Diseño** (26-nov a 11-dic-2026): entrega **H2** (diseño y planificación).
  - **Fase 3 · Planificación** (10-dic a 21-ene-2027): entrega **H2**.
  - **Fase 4 · Implementación** (21-ene a 31-mar-2027): desarrollo, pruebas y despliegue.

  ## 8. Glosario

  | Término    | Definición                                                   | Sinónimos que NO uso                                         |
  | ---------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | Rutina     | Secuencia ordenada de ejercicios con sus series y repeticiones. | Plan.                                                        |
  | Serie      | Unidad de trabajo dentro de un ejercicio (con su carga y repeticiones). | Set.                                                         |
  | Repetición | Una ejecución de la serie.                                   | —                                                            |
  | Carga      | Peso o resistencia aplicada en una serie.                    | Peso (uso «peso» solo como adjetivo: peso corporal).         |
  | Sesión     | Registro de una actuación de entrenamiento.                  | Entrenamiento (lo uso como acción/adjetivo, no como sinónimo del registro). |

  ---

  ## Criterios de evaluación de este documento (RA1, texto literal)

  - **1a)** Se han clasificado las empresas del sector por sus características organizativas y el tipo de producto o servicio que ofrecen.
  - **1b)** Se han caracterizado las empresas tipo indicando la estructura organizativa y las funciones de cada departamento.
  - **1c)** Se han identificado las necesidades más demandadas a las empresas.
  - **1d)** Se han valorado las oportunidades de negocio previsibles en el sector.
  - **1e)** Se ha identificado el tipo de proyecto requerido para dar respuesta a las demandas previstas.
  - **1f)** Se han determinado las características específicas requeridas al proyecto.
  - **1g)** Se han determinado las obligaciones fiscales, laborales y de prevención de riesgos y sus condiciones de aplicación.
  - **1h)** Se han identificado posibles ayudas o subvenciones para la incorporación de nuevas tecnologías de producción o de servicio que se proponen.
  - **1i)** Se ha elaborado el guión de trabajo que se va a seguir para la elaboración del proyecto.
