# Re-generación de la base de datos

Si usted necesita re-generar la base de datos de grafos por completo, puede configurar Linkurious para que utilice una propiedad de nodo o relación como identificador alternativo, en lugar de utilizar los identificadores generados por la base de datos. Estos identificadores son almacenados en las visualizaciones para hacer referencia a los nodos y relaciones. Con identificadores alternativos, los usuarios no perderán sus visualizaciones la próxima vez que la base de datos sea re-generada. Tenga en cuenta que las propiedades utilizadas como identificador deben estar indexadas por la base de datos para su búsqueda eficiente.

Vea las claves ``alternativeNodeId`` y  ``alternativeEdgeId`` in **Comenzando > Configuración**.

Tenga en cuenta que si el identificador de almacén ha cambiado después de re-generar la base de datos, Linkurious no la reconocerá como la misma base de datos. Usted puede asignar el ``sourceKey`` previo de forma explícita en la configuración de la fuente de datos.