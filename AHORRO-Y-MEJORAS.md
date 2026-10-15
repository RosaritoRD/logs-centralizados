# 💸 Ahorro y mejoras

## Gastar menos

1. **Loki en lugar de Elasticsearch.** Elasticsearch indexa cada palabra y pide 2–4 GB de RAM. Loki indexa solo las etiquetas (contenedor, origen, job): las tres piezas juntas usan **~260 MB**. Cabe en el mismo VPS barato que tus apps, sin pagar otro servidor.
2. **Retención de 30 días**, igual a `reject_old_samples_max_age`. Si aceptas más días de los que guardas, gastas CPU ingiriendo líneas que se borran al momento.
3. **`mem_limit` en los tres servicios.** No es para ahorrar dinero, sino para que el visor nunca obligue a ampliar el servidor ni tumbe lo que vigila.
4. **Sin servicios de pago.** Todo es software libre (Grafana, Loki, Alloy) y no hay ningún SaaS de logs con cuota mensual.

## Hacerlo mejor

1. **Un compose aparte**, para que el visor sobreviva cuando falla lo demás.
2. **Pon el subdominio de Grafana fuera del nginx de tu web.** Si tu web se rompe, el acceso a los logs no se rompe con ella.
3. **Mira primero el panel "Accesos que SÍ funcionaron".** Mil intentos fallidos son ruido; un acceso correcto que no reconoces es lo que importa.
4. **Haz copia de seguridad de esta carpeta.** Los dashboards son archivos: si reinstalas el servidor, vuelves a tenerlo todo con `docker compose up -d`.
5. **Ideas para ampliarlo:** alertas por Telegram cuando un contenedor escupa errores, un panel de nginx 4xx/5xx o métricas con Prometheus.
