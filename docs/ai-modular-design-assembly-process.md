# Diseño modular asistido por IA: producto, instalaciones y operación

Esta propuesta amplía el ciclo MBSE → CAD → CAM → CAS de JFXOSMS con una vista completa de diseño, industrialización, ensamblaje, automatización, despliegue y mejora. Vincula AI-INV, AI-LINE, AI-DSI, el coordinador de planes, MES y gateway industrial descritos en el README. Los servicios, instalaciones y procesos son propuestas de ingeniería; no se declara su implementación ni resultados de pruebas.

[Diagrama Drawio editable](../MBSE/CAS/Drawio/JFXOSMS_AI_Assisted_Modular_Design_Assembly_End_to_End.drawio) · [20 requisitos de proceso y aceptación](ai-modular-process-verification.csv) · [Manifest de referencias CAD](modular-process-cad-sources.json).

## Las doce páginas

| Página | Contenido |
| --- | --- |
| 01 | Ciclo completo: misión → requisitos/riesgos → arquitectura → concepto → CAD/EBOM → CAS → CAM/MBOM → inventario/programación → producción → integración/pruebas → despliegue → mantenimiento/mejora. |
| 02 | Diseño del buque multipropósito: misión, arquitectura naval, casco, distribución, hidroestática, estabilidad, estructura, propulsión, servicios, bloques y construcción. |
| 03 | Construcción/integración en dique seco flotante: seleccionar ruta, verificar compatibilidad, diseñar apoyos y estados de carga, preparar servicios, integrar, probar y poner a flote. |
| 04 | Ensamblaje naval, mecatrónica automotriz y variante anfibia VTOL: diseño para fabricación/montaje, simulación, CAM, piezas, subensambles, integración y gates de ensayo. |
| 05 | Producción preliminar en hangar subterráneo, con servicios, layout, pruebas permitidas, configuración de transporte, elevador y salida a superficie. |
| 06 | Traslado a MOAB semisumergible, carga/sujeción, integración en hangar de plataforma, elevador interno a cubierta y ensayos autorizados. |
| 07 | IA e industria: datos → recomendación → restricciones → aprobación → MES → gateway → PLC/robots → SCADA → mejora. |
| 08 | Granjas flotantes y proveedores → recepción en buque → planta higiénica modular → control de lote → distribución. |
| 09 | Agua envasada, barras de cereal, carne de soya, hamburguesas de gluten, germen de trigo, miel, leche, yogurt probiótico y productos con huevo. |
| 10 | Rutas separadas de calificación y logística para ayuda humanitaria y alimentos de misión espacial. |
| 11 | Hilo digital, gates y evidencias para producto, dique, hangar/elevadores/MOAB y alimentos. |
| 12 | Correspondencia de nueve referencias CAD de jfxotbs, jfxfmis, jfxai4bss y jfxmbdss. |

Las flechas sólidas muestran secuencia o intercambio principal; las discontinuas muestran relaciones entre ramas o filas. Cada página detalla una vista: no implica que un catálogo de productos se procese como una única secuencia. La mejora de L12 realimenta requisitos, modelos y planes mediante control de cambios. Los diagramas existentes de JFXOSMS se conservan.

## Producto e instalaciones se diseñan juntos

El CAD debe demostrar accesibilidad, tolerancias, uniones, rutas de montaje y extracción. EBOM se transforma en MBOM y operaciones/útiles; CAS evalúa física y flujo productivo, mientras CAM prepara fabricación y tareas de robots. La IA propone alternativas y planes con fuentes y límites; la autoridad del dominio aprueba. La configuración as-built y los resultados reales alimentan modelos y futuras revisiones.

Para el **buque**, las cargas de talleres, planta alimentaria, consumibles y módulos se incorporan a masa/CG, estabilidad, estructura, energía y servicios desde el diseño conceptual. Antes de construir se aprueban casos de carga y presupuestos. El dique flotante es un activo distinto: se valida su compatibilidad y el soporte del casco para cada fase. Se contemplan dos rutas alternativas: construir sobre dique emergido apto o recibir un casco ya flotable y vararlo. Las imágenes citadas no identifican un dique concreto; su selección y diseño de apoyos/maniobras son trabajo propuesto.

Para **mecatrónica automotriz y aeronave anfibia VTOL**, el ciclo completo de página 01 se concreta mediante diseño para ensamblaje, bancos y metrología de página 04. La producción preliminar ocurre en el hangar subterráneo propuesto; la configuración con cuna debe ser compatible con el elevador y el transporte hasta el punto de embarque. Después se integra en la plataforma MOAB. El elevador terrestre y el elevador interior de MOAB son activos independientes, con capacidades y criterios propios. La conexión física y el modo de traslado entre emplazamientos no aparecen definidos en los CAD: rampa, grúa o transporte intermedio se seleccionan mediante estudio de interfaz, no se presuponen.

MOAB significa **Modular Offshore Base** en CAD-07. Su cubierta, hangar interior, módulos flotantes y elevador sirven de referencia visual. El aeropuerto flotante de jfxotbs y la plataforma offshore de jfxai4bss son conceptos relacionados, no configuraciones idénticas. El transporte anfibio de CAD-08 y el VTOL Pegasus de CAD-09 tampoco son una aeronave única: combinarlos es una variante solicitada que necesita su propio diseño de estructura, flotación, energía y modos de control. La ilustración Pegasus no establece flotación propia y el transporte anfibio no establece VTOL.

Los límites dimensionales, masas, cargas concentradas, capacidad de elevadores/dique, estabilidad, movimientos relativos, condiciones ambientales y ensayos aire/agua/tierra permanecen TBD por configuración. El hangar no implica autorización para ensayos de vuelo; MOAB no implica habilitación aeronáutica. Cada gate necesita una revisión del activo, sitio y operación.

## Planta alimentaria embarcada

Se proponen módulos separados de agua, cereales/proteínas, lácteos/ovo, conservación, envasado, laboratorio y almacenamiento. Se dimensionan con la misión y el buque: throughput, masa/energía/agua, frío, personal, limpieza, residuos y distribución. Los talleres, soldadura y combustibles necesitan segregación respecto a ingredientes, aire, circuitos y zonas higiénicas. El gemelo registra recetas, lotes, condiciones y estado de calidad; las líneas ejecutan únicamente procesos aprobados.

| Producto | Cadena propuesta y decisión pendiente |
| --- | --- |
| Agua desalinizada envasada | Fuente de agua, tratamiento seleccionado, acondicionamiento, seguridad del agua, potabilidad y envase; no se libera por el solo hecho de pasar por desalación. |
| Barras de cereal | Ingredientes y receta nutricional trazados, conformado, conservación y envase validados según destino. |
| Carne de soya | Proteína/soya trazada; definir si se texturiza a bordo o se recibe texturizada; formular, procesar y conservar. |
| Hamburguesas de gluten | Trigo/gluten trazado; receta, formado, proceso y conservación; especificación explícita de gluten. |
| Germen de trigo | Germen separado o recibido, estabilización y control de conservación/oxidación; no se confunde con brotes germinados. |
| Miel de abeja | Cadena apícola identificada; no se atribuye su origen directamente a cultivos hidropónicos. |
| Leche fresca | Cadena ganadera/proveedor, tratamiento, envase y frío validados; no se supone estabilidad a temperatura ambiente. |
| Yogurt probiótico | Leche y cultivo identificados, fermentación, frío/envase y verificación de identidad/viabilidad; no se inventan beneficios de salud. |
| Productos con huevo | Cadena avícola/proveedor y receta/proceso propios; recepción, tratamiento y conservación aprobados. |

Las granjas verticales/aterrazadas flotantes aportan cultivos compatibles con su diseño y capacidad. Soya/trigo requieren evaluación de cultivo, maduración, separación y rendimiento o suministro alternativo terrestre. Leche, huevos y miel necesitan proveedores o módulos ganaderos, avícolas/apícolas diseñados y evaluados por separado; no se presuponen en los CAD agrícolas. Los peces/moluscos de CAD-05 no se incorporan a este catálogo ovo-lacto-vegetariano.

Para ayuda humanitaria se especifican población, preparación, conservación, entrega, alérgenos y retiro de lotes según la infraestructura disponible. Para astronautas se desarrolla y califica cada fórmula/proceso/envase conforme al programa de misión: no se transforma automáticamente una receta naval ni un lácteo fresco en alimento apto para vuelo. Las tecnologías de estabilización propuestas se evalúan por producto y sus cambios requieren revalidación.

## Trazabilidad, presupuestos y aceptación

El CSV contiene PROC-01…PROC-20, nodos del diagrama, obligación propuesta, método I/A/T/D, criterio de aceptación, rol responsable y evidencia prevista. Todas las evidencias figuran pendientes. Antes de ejecutar el plan, asignar personas/fechas y aprobar valores de capacidad, desempeño y calidad, límites de operación y métodos de ensayo.

El hilo digital enlaza requisito → CAD/interfaz/EBOM → MBOM/receta/operación → escenario/snapshot/modelo/política → recomendación/decisión → orden → pieza/lote/as-built → evidencia. Se mantiene `plan_revision`, vigencia, idempotencia y restricciones independientes de la recomendación. Las funciones protectoras permanecen bajo control local validado. Las no conformidades retienen piezas/lotes; cambios de módulo, receta o política se revisan por su efecto en la aceptación y permiten retorno a una base validada.

## Fuentes y alcance de la referencia

La arquitectura, la selección de módulos y las rutas de montaje son propuestas nuevas para JFXOSMS. Los CAD sustentan únicamente elementos ilustrados y relaciones conceptuales; no se copian sus imágenes en este repositorio. Los enlaces fijados a commit y los Git blob SHA aparecen en el manifest.

Las referencias técnicas siguientes orientan la definición del trabajo de validación, sin constituir una selección completa de normas ni una certificación:

- [NASA — Space Food Systems](https://www.nasa.gov/directorates/esdmd/hhp/space-food-systems/): referencia de desarrollo, evaluación, envases y vida útil alimentaria. La propuesta asigna la aceptación espacial al programa responsable.
- [FAO — GHP and HACCP Toolbox](https://www.fao.org/good-hygiene-practices-haccp-toolbox/en): referencia de buenas prácticas y análisis de peligros. Se propone un plan específico por planta/producto, con controles y validación propios.
- [WHO — Safe drinking-water from desalination](https://www.who.int/publications/i/item/WHO-HSE-WSH-11.03): referencia de evaluación/gestión de riesgos del agua desalinizada. Se incorpora una aceptación de potabilidad separada del funcionamiento del equipo.
- [ABS — Steel Floating Dry Docks, edición 2022](https://ww2.eagle.org/content/dam/eagle/rules-and-guides/current/special_service/11_steel_floating_drydocks_2022/dry-dock-rules-jan22.pdf): referencia para evaluar compatibilidad de capacidad y cargas/apoyos. No se adopta como edición normativa definitiva; verificar reglas aplicables con responsables del dique y del buque.

## Referencias CAD revisadas

| ID | Proyecto y archivo | Aplicación |
| --- | --- | --- |
| CAD-01 | [jfxotbs / modular-underground-hangar-digital-twin.jpg](https://github.com/robotics-intelligent-systems/jfxotbs/blob/42918ec74a33107517e7275cd853342e111ab78a/MBSE/CAD/modular-underground-hangar-digital-twin.jpg) | Hangar y elevador terrestre |
| CAD-02 | [jfxotbs / open-modular-mega-floating-airport.jpg](https://github.com/robotics-intelligent-systems/jfxotbs/blob/42918ec74a33107517e7275cd853342e111ab78a/MBSE/CAD/open-modular-mega-floating-airport.jpg) | Aeropuerto flotante relacionado |
| CAD-03 | [jfxfmis / Overall-3D-view-of-the-Proposed-Multi-level-Floating-Farm-MFF.jpg](https://github.com/robotics-intelligent-systems/jfxfmis/blob/84aa99b5687758cf839b3bc21a1af6fd72715e5b/MBSE/CAD/Overall-3D-view-of-the-Proposed-Multi-level-Floating-Farm-MFF.jpg) | Granja vertical multinivel |
| CAD-04 | [jfxfmis / modular-floating-farm-island-digital-twin.jpg](https://github.com/robotics-intelligent-systems/jfxfmis/blob/84aa99b5687758cf839b3bc21a1af6fd72715e5b/MBSE/CAD/modular-floating-farm-island-digital-twin.jpg) | Isla agrícola modular |
| CAD-05 | [jfxfmis / offshore-blue-economy-open-source-digital-twins-concept-v1.jpg](https://github.com/robotics-intelligent-systems/jfxfmis/blob/84aa99b5687758cf839b3bc21a1af6fd72715e5b/MBSE/CAD/offshore-blue-economy-open-source-digital-twins-concept-v1.jpg) | Logística marina / terminal relacionado |
| CAD-06 | [jfxai4bss / self-propelled-twin-hulled-semi-submersible-platform.jpg](https://github.com/robotics-intelligent-systems/jfxai4bss/blob/b1ec2ef9f8d5287c26aa1c3b5aec62bfd4e85c42/MBSE/CAD/self-propelled-twin-hulled-semi-submersible-platform.jpg) | Plataforma offshore relacionada |
| CAD-07 | [jfxmbdss / mobile-offshore-base-digital-twin.jpg](https://github.com/robotics-intelligent-systems/jfxmbdss/blob/7075e95c6eea70b66dbd6a39edce18229cbd1f5e/MBSE/CAD/mobile-offshore-base-digital-twin.jpg) | MOAB, hangar interior y elevador |
| CAD-08 | [jfxmbdss / hydrogen-hybrid-amphibious-transport-concept.jpg](https://github.com/robotics-intelligent-systems/jfxmbdss/blob/7075e95c6eea70b66dbd6a39edce18229cbd1f5e/MBSE/CAD/hydrogen-hybrid-amphibious-transport-concept.jpg) | Transporte anfibio de referencia |
| CAD-09 | [jfxotbs / OpenTwin_VTOL_Rescue_LH2_Cutaway_Concept_v1.jpg](https://github.com/robotics-intelligent-systems/jfxotbs/blob/42918ec74a33107517e7275cd853342e111ab78a/MBSE/CAD/OpenTwin_VTOL_Rescue_LH2_Cutaway_Concept_v1.jpg) | VTOL Pegasus de referencia |
