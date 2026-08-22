# Diccionario de datos — Financiera Andes

> Datos **100% sintéticos** generados para el curso *Modelador de Riesgo de Crédito*
> (Academia Bayes). Ninguna persona ni institución real está representada.

Panel mensual: 2023-07 a 2026-06. Montos en CLP.

## clientes (andes_clientes)
| Columna | Descripción |
|---|---|
| id_cliente | Identificador único del cliente |
| fecha_alta_cliente | Mes de alta en la institución (YYYY-MM) |
| edad | Edad en años al inicio del panel |
| sexo | M / F |
| region | Región de residencia (Chile) |
| estado_civil | soltero / casado / divorciado / viudo |
| nivel_educacional | básica / media / técnica / universitaria / postgrado |
| tipo_empleo | dependiente / independiente / jubilado |
| renta_liquida | Renta líquida mensual declarada (CLP). Puede venir vacía |
| n_dependientes | Número de cargas familiares |

## solicitudes (andes_solicitudes)
| Columna | Descripción |
|---|---|
| id_solicitud | Identificador de la solicitud |
| id_cliente | Cliente que solicita |
| fecha_solicitud | Mes de la solicitud (YYYY-MM) |
| monto_solicitado | Monto del crédito de consumo (CLP) |
| plazo_meses | Plazo en meses |
| destino | Uso declarado del crédito |
| canal | sucursal / web / app |
| aprobada | La solicitud fue aprobada y cursada |
| estado_actual | Estado del crédito **a la fecha de corte 2026-06** |
| marca_fraude | Fraude confirmado posteriormente |

## comportamiento_mensual (andes_comportamiento)
| Columna | Descripción |
|---|---|
| id_cliente, mes | Llave panel (YYYY-MM) |
| saldo_linea / cupo_linea | Saldo y cupo de línea de crédito (CLP) |
| saldo_tc / cupo_tc | Saldo y cupo de tarjeta de crédito (CLP) |
| saldo_consumo | Saldo vigente de créditos de consumo en cuotas |
| dias_mora | Días de mora del cliente al cierre del mes |
| monto_facturado / monto_pagado | Facturación y pago del mes |
| abonos_cuenta | Abonos totales a cuentas del cliente en el mes |
| saldo_ahorro | Saldo de ahorro/vista al cierre |
| n_productos | Número de productos vigentes |

## bureau_mensual (andes_bureau)
| Columna | Descripción |
|---|---|
| id_cliente, mes | Llave panel (YYYY-MM) |
| deuda_otras_inst | Deuda en otras instituciones (CLP) |
| n_otras_inst | Número de otras instituciones con deuda |
| consultas_mes | Consultas al bureau en el mes |
| peor_mora_sistema | Peor mora del cliente en el sistema (0/30/60/90) |
