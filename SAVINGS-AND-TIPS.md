# 💸 Savings and tips

## Spend less

1. **Loki instead of Elasticsearch.** Elasticsearch indexes every word and wants 2–4 GB of RAM. Loki indexes only the labels (container, source, job): all three pieces together use **~260 MB**. It fits on the same cheap VPS as your apps, with no extra server to pay for.
2. **30-day retention**, equal to `reject_old_samples_max_age`. If you accept more days than you keep, you burn CPU ingesting lines that get deleted right away.
3. **`mem_limit` on all three services.** Not to save money, but so the viewer never forces you to upgrade the server or takes down what it's watching.
4. **No paid services.** Everything is free software (Grafana, Loki, Alloy) and there's no logging SaaS with a monthly fee.

## Do it better

1. **A separate compose file**, so the viewer survives when everything else fails.
2. **Keep Grafana's subdomain outside your website's nginx.** If your site breaks, access to the logs doesn't break with it.
3. **Look at the "successful logins" panel first.** A thousand failed attempts are noise; a successful login you don't recognize is what matters.
4. **Back up this folder.** The dashboards are files: if you reinstall the server, you get everything back with `docker compose up -d`.
5. **Ideas to extend it:** Telegram alerts when a container starts spitting errors, an nginx 4xx/5xx panel, or metrics with Prometheus.
