# Assessoria 3.0 — Energy Intelligence

Aplicación Next.js para importar puntos de suministro, localizar CUPS por dirección y consultar consumos, potencias, energía reactiva, alertas y oportunidades comerciales.

## Uso

```bash
npm install
npm run dev
```

Abre http://localhost:3000 y pulsa **Importar Excel**. Por defecto se muestra un suministro *ficticio* bien identificado para conocer la interfaz. Se admite XLSX, XLS y CSV; se prioriza la hoja `Page1` y se conserva la totalidad de las columnas de origen.

## Vercel

Sube el proyecto a GitHub, importa el repositorio en Vercel (Framework: Next.js) y despliega. No hay variables de entorno obligatorias. También puedes ejecutar `npm run build` localmente.

## Estado funcional y límites

- Importador Excel (lectura en navegador), buscador global por CUPS / dirección / localidad, panel, gráficos por mes, vista técnica integral.
- Alertas BIE/APM/derechos, impagos, contratabilidad, lecturas antiguas y ausencia de consumo. Se basan solo en el archivo.
- Simulador del término fijo de potencia: seis periodos, precios en €/kW/día, coste de cambio, diferencia anual y periodo de recuperación **parcial**. No calcula excesos o optimización regulatoria sin curvas y reglas específicas.
- Reactiva anual y mensual; cálculo de penalización omitido hasta contar con datos suficientes.
- Ofertas manuales: comparación del término de energía únicamente si todos los precios utilizados son iguales; si hay discriminación por periodos, pide desglose medido. Coste fijo si las potencias contratadas están completas. No presenta impuestos/cargos inventados.
- Radar comercial y ficha de oportunidad con responsable, notas y registro manual de llamadas; exportación CSV y guardar vista como PDF mediante impresión.
- Las ofertas, anotaciones, marcas y llamadas se guardan **solo en localStorage del dispositivo**. Los Excel importados se mantienen solo en memoria del navegador; recarga = nueva importación.
- No incluye autenticación, base de datos, sincronización multiusuario, conexión al CRM, procesado de curvas cuarto-horarias, motores normativos de optimización real, alerta automática persistente ni generación de PDFs del lado servidor. Para producción multiusuario hay que implantar estas funciones.
- El archivo XLSX real mencionado en el texto original **no se adjuntó** en este turno; el mapeo está basado en los nombres de columna proporcionados. Verificar encabezados exactos y formatos de fechas con una muestra real antes de producción.

## Privacidad y calidad

Los ficheros no se envían a ningún servidor por la aplicación. No utilices la versión actual como repositorio persistente de datos ni como cálculo vinculante de facturación. Para un entorno comercial, añadir login, permisos por empleado, base de datos y auditoría.
