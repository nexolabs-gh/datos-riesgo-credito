# Diccionario — matrices modelables A y B

> Datos 100% sintéticos para el curso Modelador de Riesgo de Crédito. 
> Banco Austral y Financiera Andes comparten este esquema.

## Metadatos, partición y target

| variable        | descripción                                                   |
|:----------------|:--------------------------------------------------------------|
| id_solicitud    | Identificador único de la solicitud.                          |
| id_cliente      | Identificador del cliente; puede repetirse en TTD.            |
| fecha_solicitud | Mes de la solicitud en formato YYYY-MM.                       |
| cohorte         | Cohorte de la solicitud en formato YYYY-MM.                   |
| muestra         | Partición original: DEV, HO, OOT o TTD.                       |
| malo            | Target: 1 si alcanza 90+ DPD en 12 meses; nulo sin desempeño. |
| indeterminado   | Verdadero si la peor mora está entre 30 y 89 DPD.             |

## Variables candidatas de la fábrica

| variable                 | serie_origen                        | agregador   | ventana       | tipo                    | dtype   |
|:-------------------------|:------------------------------------|:------------|:--------------|:------------------------|:--------|
| antiguedad_meses         | solicitud / maestro                 | —           | t0            | demográfica / solicitud | int64   |
| monto_solicitado         | solicitud / maestro                 | —           | t0            | demográfica / solicitud | float64 |
| plazo_meses              | solicitud / maestro                 | —           | t0            | demográfica / solicitud | int64   |
| destino                  | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| canal                    | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| dias_mora_max_3m         | dias_mora                           | max         | [t0-3, t0-1]  | ventana                 | float64 |
| dias_mora_max_6m         | dias_mora                           | max         | [t0-6, t0-1]  | ventana                 | float64 |
| dias_mora_max_12m        | dias_mora                           | max         | [t0-12, t0-1] | ventana                 | float64 |
| dias_mora_prom_3m        | dias_mora                           | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| dias_mora_prom_6m        | dias_mora                           | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| dias_mora_prom_12m       | dias_mora                           | prom        | [t0-12, t0-1] | ventana                 | float64 |
| n_meses_mora_3m          | en_mora                             | suma        | [t0-3, t0-1]  | ventana                 | float64 |
| n_meses_mora_6m          | en_mora                             | suma        | [t0-6, t0-1]  | ventana                 | float64 |
| n_meses_mora_12m         | en_mora                             | suma        | [t0-12, t0-1] | ventana                 | float64 |
| meses_desde_mora_12m     | en_mora                             | recencia    | [t0-12, t0-1] | ventana                 | float64 |
| uso_linea_prom_3m        | uso_linea                           | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| uso_linea_prom_6m        | uso_linea                           | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| uso_linea_prom_12m       | uso_linea                           | prom        | [t0-12, t0-1] | ventana                 | float64 |
| uso_linea_max_3m         | uso_linea                           | max         | [t0-3, t0-1]  | ventana                 | float64 |
| uso_linea_max_6m         | uso_linea                           | max         | [t0-6, t0-1]  | ventana                 | float64 |
| uso_linea_max_12m        | uso_linea                           | max         | [t0-12, t0-1] | ventana                 | float64 |
| uso_tc_prom_3m           | uso_tc                              | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| uso_tc_prom_6m           | uso_tc                              | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| uso_tc_prom_12m          | uso_tc                              | prom        | [t0-12, t0-1] | ventana                 | float64 |
| uso_tc_max_3m            | uso_tc                              | max         | [t0-3, t0-1]  | ventana                 | float64 |
| uso_tc_max_6m            | uso_tc                              | max         | [t0-6, t0-1]  | ventana                 | float64 |
| uso_tc_max_12m           | uso_tc                              | max         | [t0-12, t0-1] | ventana                 | float64 |
| saldo_consumo_prom_3m    | saldo_consumo                       | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| saldo_consumo_prom_6m    | saldo_consumo                       | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| saldo_consumo_prom_12m   | saldo_consumo                       | prom        | [t0-12, t0-1] | ventana                 | float64 |
| saldo_consumo_delta_6m   | saldo_consumo                       | delta       | [t0-6, t0-1]  | ventana                 | float64 |
| saldo_consumo_delta_12m  | saldo_consumo                       | delta       | [t0-12, t0-1] | ventana                 | float64 |
| deuda_interna_prom_3m    | deuda_interna                       | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| deuda_interna_prom_6m    | deuda_interna                       | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| deuda_interna_prom_12m   | deuda_interna                       | prom        | [t0-12, t0-1] | ventana                 | float64 |
| deuda_interna_max_3m     | deuda_interna                       | max         | [t0-3, t0-1]  | ventana                 | float64 |
| deuda_interna_max_6m     | deuda_interna                       | max         | [t0-6, t0-1]  | ventana                 | float64 |
| deuda_interna_max_12m    | deuda_interna                       | max         | [t0-12, t0-1] | ventana                 | float64 |
| deuda_total_prom_3m      | deuda_total                         | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| deuda_total_prom_6m      | deuda_total                         | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| deuda_total_prom_12m     | deuda_total                         | prom        | [t0-12, t0-1] | ventana                 | float64 |
| deuda_total_delta_6m     | deuda_total                         | delta       | [t0-6, t0-1]  | ventana                 | float64 |
| deuda_total_delta_12m    | deuda_total                         | delta       | [t0-12, t0-1] | ventana                 | float64 |
| abonos_prom_3m           | abonos_cuenta                       | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| abonos_prom_6m           | abonos_cuenta                       | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| abonos_prom_12m          | abonos_cuenta                       | prom        | [t0-12, t0-1] | ventana                 | float64 |
| abonos_delta_6m          | abonos_cuenta                       | delta       | [t0-6, t0-1]  | ventana                 | float64 |
| abonos_delta_12m         | abonos_cuenta                       | delta       | [t0-12, t0-1] | ventana                 | float64 |
| pagos_3m                 | monto_pagado                        | suma        | [t0-3, t0-1]  | ventana                 | float64 |
| pagos_6m                 | monto_pagado                        | suma        | [t0-6, t0-1]  | ventana                 | float64 |
| pagos_12m                | monto_pagado                        | suma        | [t0-12, t0-1] | ventana                 | float64 |
| facturacion_3m           | monto_facturado                     | suma        | [t0-3, t0-1]  | ventana                 | float64 |
| facturacion_6m           | monto_facturado                     | suma        | [t0-6, t0-1]  | ventana                 | float64 |
| facturacion_12m          | monto_facturado                     | suma        | [t0-12, t0-1] | ventana                 | float64 |
| saldo_ahorro_prom_3m     | saldo_ahorro                        | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| saldo_ahorro_prom_6m     | saldo_ahorro                        | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| saldo_ahorro_prom_12m    | saldo_ahorro                        | prom        | [t0-12, t0-1] | ventana                 | float64 |
| n_productos_prom_3m      | n_productos                         | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| n_productos_prom_6m      | n_productos                         | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| n_productos_prom_12m     | n_productos                         | prom        | [t0-12, t0-1] | ventana                 | float64 |
| deuda_otras_prom_3m      | deuda_otras_inst                    | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| deuda_otras_prom_6m      | deuda_otras_inst                    | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| deuda_otras_prom_12m     | deuda_otras_inst                    | prom        | [t0-12, t0-1] | ventana                 | float64 |
| deuda_otras_max_3m       | deuda_otras_inst                    | max         | [t0-3, t0-1]  | ventana                 | float64 |
| deuda_otras_max_6m       | deuda_otras_inst                    | max         | [t0-6, t0-1]  | ventana                 | float64 |
| deuda_otras_max_12m      | deuda_otras_inst                    | max         | [t0-12, t0-1] | ventana                 | float64 |
| delta_deuda_otras_6m     | deuda_otras_inst                    | delta       | [t0-6, t0-1]  | ventana                 | float64 |
| n_otras_inst_prom_3m     | n_otras_inst                        | prom        | [t0-3, t0-1]  | ventana                 | float64 |
| n_otras_inst_prom_6m     | n_otras_inst                        | prom        | [t0-6, t0-1]  | ventana                 | float64 |
| n_otras_inst_prom_12m    | n_otras_inst                        | prom        | [t0-12, t0-1] | ventana                 | float64 |
| peor_mora_sistema_3m     | peor_mora_sistema                   | max         | [t0-3, t0-1]  | ventana                 | float64 |
| peor_mora_sistema_6m     | peor_mora_sistema                   | max         | [t0-6, t0-1]  | ventana                 | float64 |
| peor_mora_sistema_12m    | peor_mora_sistema                   | max         | [t0-12, t0-1] | ventana                 | float64 |
| n_meses_mora_sistema_3m  | en_mora_sistema                     | suma        | [t0-3, t0-1]  | ventana                 | float64 |
| n_meses_mora_sistema_6m  | en_mora_sistema                     | suma        | [t0-6, t0-1]  | ventana                 | float64 |
| n_meses_mora_sistema_12m | en_mora_sistema                     | suma        | [t0-12, t0-1] | ventana                 | float64 |
| consultas_3m             | consultas_mes                       | suma        | [t0-3, t0-1]  | ventana                 | float64 |
| consultas_6m             | consultas_mes                       | suma        | [t0-6, t0-1]  | ventana                 | float64 |
| consultas_12m            | consultas_mes                       | suma        | [t0-12, t0-1] | ventana                 | float64 |
| meses_desde_consulta_12m | consultas_mes                       | recencia    | [t0-12, t0-1] | ventana                 | float64 |
| dias_mora_ult            | dias_mora                           | foto        | t0-1          | foto                    | float64 |
| saldo_linea_ult          | saldo_linea                         | foto        | t0-1          | foto                    | float64 |
| cupo_linea_ult           | cupo_linea                          | foto        | t0-1          | foto                    | float64 |
| saldo_tc_ult             | saldo_tc                            | foto        | t0-1          | foto                    | float64 |
| cupo_tc_ult              | cupo_tc                             | foto        | t0-1          | foto                    | float64 |
| saldo_consumo_ult        | saldo_consumo                       | foto        | t0-1          | foto                    | float64 |
| saldo_ahorro_ult         | saldo_ahorro                        | foto        | t0-1          | foto                    | float64 |
| deuda_otras_inst_ult     | deuda_otras_inst                    | foto        | t0-1          | foto                    | float64 |
| n_productos_ult          | n_productos                         | foto        | t0-1          | foto                    | float64 |
| peor_mora_sistema_ult    | peor_mora_sistema                   | foto        | t0-1          | foto                    | float64 |
| uso_linea_ult            | uso_linea                           | foto        | t0-1          | foto                    | float64 |
| uso_tc_ult               | uso_tc                              | foto        | t0-1          | foto                    | float64 |
| carga_financiera         | deuda_ult / abonos_prom_6m          | ratio       | mixta         | ratio                   | float64 |
| pago_sobre_fact_6m       | pagos_6m / facturacion_6m           | ratio       | mixta         | ratio                   | float64 |
| pago_sobre_fact_12m      | pagos_12m / facturacion_12m         | ratio       | mixta         | ratio                   | float64 |
| deuda_int_sobre_sistema  | deuda_interna_ult / deuda_total_ult | ratio       | mixta         | ratio                   | float64 |
| ahorro_sobre_ingreso     | saldo_ahorro_ult / abonos_prom_6m   | ratio       | mixta         | ratio                   | float64 |
| monto_sobre_ingreso      | monto_solicitado / abonos_prom_6m   | ratio       | mixta         | ratio                   | float64 |
| cuota_est_sobre_ingreso  | (monto/plazo) / abonos_prom_6m      | ratio       | mixta         | ratio                   | float64 |
| edad                     | solicitud / maestro                 | —           | t0            | demográfica / solicitud | int64   |
| sexo                     | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| region                   | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| estado_civil             | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| nivel_educacional        | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| tipo_empleo              | solicitud / maestro                 | —           | t0            | demográfica / solicitud | object  |
| renta_liquida            | solicitud / maestro                 | —           | t0            | demográfica / solicitud | float64 |
| n_dependientes           | solicitud / maestro                 | —           | t0            | demográfica / solicitud | int64   |
| renta_vs_abonos          | renta_liquida / abonos_prom_6m      | ratio       | mixta         | ratio                   | float64 |

Todas las ventanas terminan en t0-1. La matriz conserva las 108 candidatas; 
la selección corresponde a la corrida de modelación.
