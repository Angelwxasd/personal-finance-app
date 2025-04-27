# personal-finance-app

Esto es un pequeño ejemplo de una aplicación de finanzas personales. 
Tiene como finalidad lo siguiente:
- LLevar un registro de gastos, ingresos e inversiones.
- Cuente con un algoritmo para pagar deudas (o sea que tú mismo lleves registro en cuánto tiempo pagarías la deuda dependiendo de la tasa de interés y del CAT), o sea que es un simulador de deudas jaja
- Que se pueda visualizar el progreso de alguna inversión (Pendiente)
- Accesos directos para registrar gastos e ingresos (Pendiente) (Widgets en el Launcher)
- La opción de formar un presupuesto y notificarme si me he excedido
- Aprender Finanzas
- Alguna forma de implementar la IA correctamente en el manejo de la aplicación




### MODELO ENTIDAD - RELACIÓN (ER)

#### Entidades y Atributos
1. Usuarios
  - id_usuario (PK)
  - nombre
  - email
  - contraseña
  - fecha_registro
2. Cuentas
  - id_cuenta (PK)
  - id_usuario (FK a Usuarios)
  - nombre
  - tipo (crédito, débito/efectivo, inversiones)
  - moneda
  - saldo
3. Configuración de Crédito
  - id_config (PK)
  - id_cuenta (FK a cuentas, único)
  - dia_corte (por ejemplo el 21 de cada mes)
  - dia_pago (la fecha límite de pago, por ejemplo el 5 de cada mes)
  - CAT (Costo Anual Total de la tarjeta de crédito)
  - tasa_interés
  - credito_total (Es decir, el límite de crédito que tenemos en la tarjeta)
4. Categorías
  - id_categoria (PK)
  - nombre (único)
  - tipo (ingreso/gasto)
5. Transacciones
  - id_transaccion (PK)
  - id_cuenta (FK a Cuentas)
  - id_categoria (FK a Categorías)
  - monto
  - descripción
  - fecha
  - tipo (ingreso/gasto/transferencia)
6. Deudas
  - id_deuda
  - id_cuenta
  - monto_inicial
  - saldo_pendiente
  - tasa_interés
  - pago_mínimo
7. Pagos
  - id_pago
  - id_deuda
  - monto
  - fecha_pago

#### RELACIONES
- Usuarios $\to$ Cuentas: 1 a N (un usuario tiene muchas cuentas)
- Cuentas $\to$ Configuración de Crédito: 1 a 1 (se refiere a que una cuenta sólo puede tener una configuración de crédito)
- Cuentas $\to$ Transacciones: 1 a N (una cuenta tiene muchas transacciones)
- Categorías $\to$ Transacciones: 1 a N (Una categoría agrupa muchas transacciones)
- Cuentas $\to$ Deudas (1:N)
- Deudas $\to$ Pagos (1:N)
- Transacciones $\to$ Deudas (N:1)



