### Descripción

- **Categoría:** Forensics (análisis de tráfico de red)
- **Enunciado:** "We found this packet capture. Recover the flag that was pilfered from the network."
- **Archivo entregado:** `shark-on-wire-2-capture.pcap` (112 318 bytes, formato pcap 2.4, Ethernet)
- **Objetivo:** encontrar la flag que fue exfiltrada escondida en el tráfico.

La captura contiene 1326 paquetes, en su mayoría UDP, mezclados con tráfico legítimo y mucho ruido deliberado.

### Solución

**1. Parseo del pcap.** No había disponibles `tshark` ni `scapy`, así que se leyó el formato pcap directamente con Python (cabecera global de 24 bytes y, por cada paquete, una cabecera de 16 bytes seguida de los datos). Se extrajeron IPs, puertos y payloads UDP.

**2. Clasificación de flujos.** Había tráfico de fondo (mDNS, SSDP, LLMNR) y varios flujos señuelo: payloads como `AAAA…`, `BBBBB`, cadenas aleatorias, la frase `academy Sure is fun!` o caracteres sueltos enviados al puerto 8888 que no forman ninguna flag coherente.

**3. Localización de los marcadores.** Dos paquetes destacaban por su contenido:

- `start`: 10.0.0.66 → 10.0.0.1, puerto destino 22
- `end`: 10.0.0.80 → 10.0.0.1, puerto destino 22

El canal encubierto queda entre ambos.

**4. Identificar dónde está el dato.** Entre `start` y `end`, los paquetes de 10.0.0.66 hacia el puerto 22 llevan siempre el mismo payload (`aaaaa`), así que el contenido no aporta nada. Lo único que varía es el **puerto origen**, con valores entre 5048 y 5125. Ese rango estrecho sugiere la codificación `puerto_origen − 5000 = código ASCII`.

**5. Decodificación.** Tomando esos 33 paquetes en orden cronológico:

```python
seg = [p for p in paquetes_entre_start_y_end
       if p.src == '10.0.0.66' and p.dport == 22]
print(''.join(chr(p.sport - 5000) for p in seg))
```

Ejemplos: 5097 → `a`, 5099 → `c`, 5100 → `d`, 5101 → `e`, 5109 → `m`, 5121 → `y`, 5123 → `{`, 5125 → `}`.

**Flag:** `academy{p1LLf3r3d_data_v1a_st3g0}`


### Notas adicionales


### Referencias
