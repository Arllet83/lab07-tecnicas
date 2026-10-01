# Tarea: Mi prompt avanzado

## Tarea elegida
Configurar una red inalámbrica (Wi-Fi) segura en una oficina pequeña, aplicando buenas prácticas de ciberseguridad en redes (cifrado WPA3, aislamiento de invitados y desactivación de SSID oculto/WPS).

## Versión 1: Prompt básico

```text
Prompt:
Escribe reglas de firewall para una red corporativa.
```

* **Técnica agregada:** Ninguna.

* **Por qué:** Establece el punto de partida directo y sin restricciones.

* **Qué mejoró:** Entrega una lista muy básica de puertos genéricos sin contexto de seguridad real.

## Versión 2: Prompt intermedio con rol y estructura

```text
Prompt:
<rol>Actúa como administrador de redes.</rol>
<tarea>Escribe reglas de firewall para bloquear tráfico malicioso.</tarea>
<formato>Usa una lista con viñetas.</formato>
```

* **Técnica agregada:** Role prompting y prompt estructurado básico.

* **Por qué:** Para darle un enfoque profesional y ordenar las instrucciones.

* **Qué mejoró:** La respuesta adopta un tono técnico y separa la tarea mediante etiquetas.

## Versión 3: Prompt final

```text
Prompt:
<rol>Actúa como analista senior de seguridad ofensiva y defensiva (SOC).</rol>
<contexto>Necesitamos blindar los accesos perimetrales de una red corporativa bloqueando protocolos vulnerables y permitiendo solo lo estrictamente necesario.</contexto>
<ejemplos>
Ejemplo de regla bloqueada:
Tráfico: Entrada | Protocolo: ICMP (Ping externo) | Acción: DROP | Motivo: Previene escaneos de red (Ping Sweep).

Ejemplo de regla permitida:
Tráfico: Entrada | Protocolo: HTTPS (Puerto 443) | Acción: ACCEPT | Motivo: Permite tráfico web seguro hacia los servidores oficiales.
</ejemplos>
<tarea>Diseña 3 reglas de firewall adicionales (una para SSH, otra para DNS y otra para bloquear Telnet) siguiendo estrictamente el formato de los ejemplos.</tarea>
<formato>Presenta las reglas en una tabla con las columnas: Tipo de Tráfico, Protocolo/Puerto, Acción y Justificación técnica.</formato>
<autocrítica>
Revisa tu tabla: ¿Incluiste la regla para bloquear Telnet (puerto 23) por ser un protocolo inseguro en texto plano? Si falta, agrégala de inmediato.
</autocrítica>
```

* **Técnica agregada:** Few-shot (ejemplos previos de entrada/salida), Role prompting avanzado, Prompt estructurado con etiquetas XML y Autocrítica integrada.

* **Por qué:** Para combinar el aprendizaje mediante ejemplos claros, la perspectiva experta, el orden estricto de etiquetas y una revisión de calidad automática que evite omisiones de seguridad críticas.

* **Qué mejoró:** El resultado se generó en un formato tabular impecable, siguiendo exactamente la estructura de los ejemplos provistos y garantizando la inclusión de puertos de riesgo gracias a la autocrítica.

## Técnicas usadas en el prompt final

| **Qué revisar** | **Parte del Prompt Final donde se aplica** |
| :--- | :--- |
| **Rol promptinkg** | <rol>Actúa como analista senior de seguridad ofensiva y defensiva (SOC).</rol> |
| **Few-shot** | Bloque <ejemplos> con casos de tráfico bloqueado y permitido |
| **Prompt estructurado** | Uso completo de etiquetas XML (<rol>, <contexto>, <ejemplos>, <tarea>, <formato>, <autocrítica>) |
| **Autocrítica** | Bloque <autocrítica>Revisa tu tabla: ¿Incluiste la regla para bloquear Telnet...?</autocrítica>|

## Evaluación del resultado

| **Criterio de evaluación** | **Cumple (Sí / No)** |
| :--- | :--- |
| **¿Define un rol técnico especializado en ciberseguridad?** | Si |
| **¿Utiliza ejemplos previos (Few-shot) para guiar la respuesta?** | Si |
| **¿Está estructurado mediante etiquetas XML y formato tabular??** | Si |
| **¿Incluye un bloque de autocrítica para verificar puertos inseguros?** | Si |


## ¿Por qué elegí estas técnicas?
Elegí estas técnicas porque el uso de Few-shot le enseña a la IA el formato exacto que requerimos mediante patrones previos; el prompt estructurado con etiquetas aísla perfectamente el contexto y las reglas; el rol aporta rigor técnico; y la autocrítica fuerza a la IA a verificar que no haya olvidado bloquear protocolos altamente vulnerables como Telnet, asegurando un resultado de nivel profesional.

