# Resultados de carga S15

Pruebas ejecutadas en modo no GUI con Apache JMeter 5.6.3 contra `GET /pets`, con rampa de 10 segundos y una iteración por usuario. El host se omite de los CSV publicados; para repetir la prueba se indica al ejecutar JMeter.

| Usuarios | Solicitudes | HTTP 200 | HTTP 500 | Errores | Promedio | P90 | Máximo | Archivo |
|---:|---:|---:|---:|---:|---:|---:|---:|---|
| 10 (repetición válida) | 10 | 10 | 0 | 0% | 446 ms | 583 ms | 604 ms | `users-10-rerun.csv` |
| 100 | 100 | 100 | 0 | 0% | 398 ms | 433 ms | 1,092 ms | `users-100.csv` |
| 1,000 | 1,000 | 1,000 | 0 | 0% | 530 ms | 602 ms | 1,073 ms | `users-1000.csv` |
| 5,000 (primera ejecución) | 5,000 | 5,000 | 0 | 0% | 447 ms | 504 ms | 1,280 ms | `users-5000.csv` |
| 5,000 (repetición) | 5,000 | 4,998 | 2 | 0.04% | 626 ms | 1,330 ms | 2,797 ms | `users-5000-top.csv` |

La repetición de 5,000 usuarios tuvo dos respuestas HTTP 500; se conserva ese resultado como tal. No se incluye la ejecución inicial de 10 usuarios porque se detuvo al detectar una configuración de bucle incorrecta.

## Ejecución

Desde esta carpeta, define el DNS o IP de destino al ejecutar la prueba:

```sh
jmeter -n -t jmeter/PlanS15.jmx -Jhost=<host> -Jusers=10 -l jmeter/result/s15/nueva-ejecucion.csv
```

Cambia `-Jusers` por `100`, `1000` o `5000` para repetir cada nivel. Usa solo un destino propio o autorizado.
