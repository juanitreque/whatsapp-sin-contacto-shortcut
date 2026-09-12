# WhatsApp sin contacto 3.0 beta 4

Abre un chat de WhatsApp con un número que no está guardado en Contactos. Funciona desde la hoja de compartir, el portapapeles o una entrada manual y siempre pide confirmación antes de abrir WhatsApp.

## Qué resuelve

- Extrae uno o varios teléfonos de texto copiado desde webs, correos o documentos.
- Normaliza espacios, guiones, puntos y paréntesis.
- Convierte `00` al formato internacional equivalente.
- Acepta números españoles sin prefijo y añade `34`.
- Reconoce códigos internacionales cuando se escriben con `+` o `00`.
- Convierte dígitos árabes, persas y de ancho completo a cifras ASCII.
- Elimina extensiones explícitas como `ext. 204`, `extensión 204` o `anexo 204`.
- Muestra una lista cuando encuentra varios candidatos.
- Abre `https://wa.me/<número>` usando exclusivamente cifras, tal como requiere WhatsApp.

El atajo **no guarda contactos, no envía mensajes y no descarga el contenido de las páginas web**.

## Instalación

1. Descarga `WhatsApp-sin-contacto-3.0-beta-4.shortcut` desde la carpeta `release`.
2. Ábrelo con la app Atajos de Apple.
3. Revisa sus acciones y pulsa «Añadir atajo».
4. Desde otra aplicación, selecciona o copia un teléfono y ejecuta «WhatsApp sin contacto 3.0 beta 4».
5. Comprueba el destinatario antes de elegir «Abrir WhatsApp».

Apple también permite distribuir un atajo mediante un enlace público de iCloud. Ese enlace se añadirá cuando se publique la versión comunitaria.

## Ejemplos

| Entrada | Destinatario normalizado |
|---|---|
| `+1 (202) 555-0123` | `+12025550123` |
| `6XX XXX XXX` | `+346XXXXXXXX` |
| `0034 (6XX) XXX-XXX` | `+346XXXXXXXX` |
| `+44 7700 900123` | `+447700900123` |
| `+١ ٢٠٢ ٥٥٥ ٠١٢٣` | `+12025550123` |
| `＋１ ２０２ ５５５ ０１２３` | `+12025550123` |
| `+1 202 555 0123 ext. 204` | `+12025550123` |

## Límites conocidos

- España es el país predeterminado. Para otros países hay que incluir `+` o `00`.
- `011 44…` y formatos como `+44 (0)20…` requieren corrección manual porque una conversión automática no sería segura en todos los países.
- Dos números extranjeros separados únicamente por espacios pueden parecer un solo número. Conviene separarlos con `/`, coma, punto y coma o salto de línea.
- Una referencia de nueve cifras que empiece por 6, 7, 8 o 9 puede parecer un número español. La confirmación final permite detectarlo antes de abrir WhatsApp.
- La validación comprueba el formato general del plan de numeración; no confirma que el número exista ni que tenga cuenta de WhatsApp.

## Validación

- 40 casos unitarios ejecutados con el motor de expresiones regulares de Apple.
- 12 recorridos completos con una copia de diagnóstico sin acción «Abrir URL».
- Firma, importación, documentación interna y variable del bucle anidado comprobadas en el editor de Atajos.

## Documentación interna

Las primeras acciones son comentarios que Atajos ignora durante la ejecución. Incluyen ficha y autores, funcionalidades, límites, historial de versiones, privacidad, créditos y licencia. Solo aparecen al abrir el atajo en el editor.

El resumen anonimizado está en `tests/verification-summary.json`.

## Privacidad y seguridad

Todo el análisis se realiza mediante acciones nativas de Atajos en el dispositivo. La única URL externa que abre la versión normal es `https://wa.me/<número>`, después de que el usuario confirme el destinatario. El número se transmite a WhatsApp cuando se abre esa URL.

## Créditos y licencia

Reconstrucción basada en el atajo compartido «Open in WhatsApp», atribuido dentro del original a `@johndoe85`.

Reconstrucción y mantenimiento de la versión 3.0: [`@juanitreque`](https://github.com/juanitreque).

Las reglas generales de numeración se derivan de `PhoneNumberMetadata.xml` del proyecto Google libphonenumber, distribuido bajo Apache License 2.0. La licencia se conserva en `LICENSES/libphonenumber-Apache-2.0.txt`.

No se asigna una licencia adicional al atajo original mientras no se confirme la autorización de su autor. Las contribuciones y redistribuciones deben conservar los créditos existentes.

## English summary

This Apple Shortcut opens a WhatsApp chat with a phone number that is not saved in Contacts. It extracts and normalizes numbers from shared text, the clipboard or manual input; supports common international formats and Unicode digits; handles multiple candidates; and always asks for confirmation. It does not save contacts or send messages automatically.

Spain is the default country. Other countries should include `+` or `00`. The final `wa.me` URL contains digits only.
