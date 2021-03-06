# Aplicando parches (patches) en proyectos.

Supongamos que hemos obtenido un código (ej. xv6-unrc) en el cual queremos incluir nuestras contribuciones y luego devolverles las modificaciones al equipo de desarrollo original.

## Herramientas diff y patch.

El comando diff muestra las diferencias entre dos archivos o múltiples archivos en diferentes
carpetas. Con el comando diff podemos generar un parche.

Ejemplo:

	Carpeta original: xv6-orig
	Carpeta nueva (con nuestras contribuciones): xv6-nuevo

	1. Generación del parche:
			
			```
			diff -rupN xv6-orig/ xv6-new/ > proj1.patch
			```

			Ahora este parche puede ser distribuido a quien lo requiera

			Nota: es conveniente antes de aplicar el parche hacer un make clean (lo cual borra 
            todos los archivos resultantes de la compilación). De esta forma el parche sólo incluirá
			las diferencias entre los programas fuentes.

	2. Aplicación del parche:
			Quien quiera aplicar el parche al código original, deberá hacer (ubicados en la carpeta que contenga los archivos a modificar), el comando
			
			```
			patch -p1 < proj1.patch
			```
			
			el cual aplicará los cambios a los archivos correspondientes.

Para más información, man diff y man patch.
