Se trata de un dataset de facturación de una empresa de medios multinacional que vende pautas publicitarias a distintos anunciantes y/o agencias de publicidad. Con estos datos se generan las facturas que se envían a los clientes. No se incluyen datos de cobranzas ni pagos. 

Row type: Tipo de facturación. --> tipo
 - Sólo nos quedamos con "Contract transmission", "Contract instalment" y "Contract prebill" 
Advertiser: Clientes que pautan --> anunciante 
Advertiser code: Código de identificación de anunciante --> codigo_anunciante
Agent: Agencia, intermediarios entre clientes y la empresa. 
Agent code: Código de identificación de agencia --> agent_code
Invoice number: Código de facturación. 
Invoice referenced: no aporta
Delivery: no aporta
Product: Producto anunciado en la pauta --> producto
Month: Mes en que se transmitió la pauta
Year: Año en que se transmitió la pauta
Recipient: Agencia. 
Contract: Codigo del sistema por cada pauta. No lo vamos a usar. 
Contract description: Comentarios sobre el contrato. No lo vamos a usar. 
Invoice amount gross: Ingresos brutos en moneda local --> ing_bruto_local
Invoice amount net: Ingresos netos (sin comisión) en moneda local --> ing_neto_local
Invoice amount gross home currency: Ingresos brutos en dólares  --> ing_bruto_dolar
Invoice amount net: Ingresos netos (sin comisión) en dólares --> ing_neto_dolar
Exchange rate: tipo de cambio de moneda local a dólar --> tipo_cambio
Invoice currency: moneda de facturación --> moneda
Tax: no lo vamos a usar
Contract amount: no lo vamos a usar (valor de referencia)
Channel: canal donde se transmite la pauta --> canal
Channel code: codigo de canal donde se transmite la pauta --> id_canal
Item start date: Fecha en que inició la pauta (MM/DD/YYYY)
Item end date: Fecha en que terminó la pauta (MM/DD/YYYY)
PO number: codigo interno del cliente (no lo vamos a usar)
SAP code: codigo de SAP (no lo vamos a usar)
Contract status: Estado del contrato --> estado_contrato
SAP G/L account code: no lo vamos a usar
Invoice amount total: igual a ingreso neto (no lo vamos a usar)
Invoice date: fecha de facturacion (MM/DD/YYYY)

CREAR: com_dolar --> ing_bruto_dolar - ing_neto_dolar
