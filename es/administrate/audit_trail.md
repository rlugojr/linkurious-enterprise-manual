# Trazas de auditoría

## Configuración

Linkurious Enterprise es distribuido con una característica de trazas de auditoría. Esta característica le permite guardar registros detallados sobre las operaciones realizadas en su base de datos de grafos por los usuarios de Linkurious Enterprise.
Para configurar el sistema de trazas de auditoría, edite el archivo `linkurious/data/config/production.json`. Añada lo siguiente al objeto:

```json
"auditTrail": {
  "enabled": true,
  "logFolder": "audit-trail",
  "fileSizeLimit": 5242880,
  "strictMode": false,
  "mode": "rw"
}
```

* **enabled** - `false`. Activa la traza de auditoría cuando es `true`.
* **logFolder** - `"audit-trail"`. Dónde guardar los archivos de registro. Esta ruta es relativa al directorio `data` situado en la raíz de la instalación de Linkurious.
* **fileSizeLimit** - `5242880`. Tamaño máximo en bytes de un archivo de registro (predeterminado: 5MB). Un nuevo archivo es creado cuando el límite es alcanzado (rotación de archivos) para evitar archivos de registro enormes.
* **strictMode** - `false`. Asegura que la operación se haya registrado antes de devolver el resultado al usuario si es `true`. Podría tener un gran impacto en la velocidad de respuesta del servidor.
* **mode** - `"rw"`. Guardar acciones de LECTURA (`"r"`), ESCRITURA (`"w"`), o ambas (`"rw"`).


## Formato de los registros
Los registros son líneas JSON. Usted puede unirlas a un sistema de gestión de registros como Log Stash para interpretarlos. Ejemplo:

```json
{"mode":"READ","date":"2015-10-11T11:05:21.888Z","user":"seb@linkurio.us","sourceKey":"2c08a4d9","action":"getEdge","params":{"edgeId":23}}
{"mode":"READ","date":"2015-10-11T11:05:21.889Z","user":"jean@linkurio.us","sourceKey":"2c08a4d9","action":"getNode","params":{"id":157}}
{"mode":"READ","date":"2015-10-11T11:05:21.910Z","user":"seb@linkurio.us","sourceKey":"2c08a4d9","action":"getNode","params":{"id":832}}
```