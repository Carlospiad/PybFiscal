# PybFiscal
Driver de Impresión en Impresoras Fiscales para comandos en script formato ixbatch compatible

Utiliza la libreria python [PyFiscalPrinter](https://github.com/reingart/pyfiscalprinter)
y permite imprimir en impresora fiscal archivos como este:




## Ejemplo de Archivo de Entrada:

```
@SetCustomerData|BRAICHUCHINCHULINCHIN  |23331234567|I|C|Rosario 4332|

@OpenFiscalReceipt|A|T
@PrintLineItem|Mouse Logitech M187|1.0|5.08|10.50|M|0.0|0|B
@PrintLineItem|Cable de Red Largo |5.0|5.10|21.00|M|0.0|0|B
@PrintLineItem|Parlantes Edifier  |1.0|5.12|21.00|M|0.0|0|B
@PrintLineItem|Teclado Microsoft  |1.0|5.12|10.50|M|0.0|0|B
@PrintLineItem|Aire Acondicionado |2.0|5.12|21.00|M|0.0|0|B
@PrintLineItem|Memoria MicroSD 26g|2.0|5.22|21.00|M|0.0|0|B
@PrintLineItem|Lector Cod Barras  |2.0|5.30|10.50|M|0.0|0|B
@PrintLineItem|Antena Parabolica  |2.0|5.33|21.00|M|0.0|0|B
@PrintLineItem|Parabolica Humana  |1.0|5.39|10.50|M|0.0|0|B
@PrintLineItem|Ensuciador HiTechie|1.0|5.44|21.00|M|0.0|0|B
@PrintLineItem|Pythonizingling    |1.0|5.46|21.00|M|0.0|0|B
@Subtotal|P|Subtotal|0|
@TotalTender|Efectivo|100.00|T|0
@CloseFiscalReceipt
```



## Ejemplo de Salida:

```
#python PybFiscal.py -t
sendCommand 42 []
sendCommand 93 ('3', '\x7f')
sendCommand 93 ('4', '\x7f')
sendCommand 93 ('5', '\x7f')
sendCommand 93 ('11', '\x7f')
sendCommand 93 ('12', '\x7f')
sendCommand 93 ('13', '\x7f')
sendCommand 93 ('14', '\x7f')
sendCommand 93 ('15', '\x7f')
sendCommand 93 ('16', '\x7f')
sendCommand 93 ('17', '\x7f')
sendCommand 93 ('18', '\x7f')
sendCommand 93 ('19', '\x7f')
sendCommand 98 ['BRAICHUCHINCHULINCHIN  ', '23331234567', 'I', 'C', 'Rosario 4332']
sendCommand 64 ['A', 'T']
sendCommand 66 ['Mouse Logitech M187', '1.0', '5.08', '10.5', 'M', '0.0', '1', 'T']
sendCommand 66 ['Cable de Red Largo ', '5.0', '5.1', '21.0', 'M', '0.0', '1', 'T']
sendCommand 66 ['Parlantes Edifier  ', '1.0', '5.12', '21.0', 'M', '0.0', '1', 'T']
sendCommand 66 ['Teclado Microsoft  ', '1.0', '5.12', '10.5', 'M', '0.0', '1', 'T']
sendCommand 66 ['Aire Acondicionado ', '2.0', '5.12', '21.0', 'M', '0.0', '1', 'T']
sendCommand 66 ['Memoria MicroSD 26g', '2.0', '5.22', '21.0', 'M', '0.0', '1', 'T']
sendCommand 66 ['Lector Cod Barras  ', '2.0', '5.3', '10.5', 'M', '0.0', '1', 'T']
sendCommand 66 ['Antena Parabolica  ', '2.0', '5.33', '21.0', 'M', '0.0', '1', 'T']
sendCommand 66 ['Parabolica Humana  ', '1.0', '5.39', '10.5', 'M', '0.0', '1', 'T']
sendCommand 66 ['Ensuciador HiTechie', '1.0', '5.44', '21.0', 'M', '0.0', '1', 'T']
sendCommand 66 ['Pythonizingling    ', '1.0', '5.46', '21.0', 'M', '0.0', '1', 'T']
sendCommand 67 []
sendCommand 68 ['Efectivo', '100.00', 'T', '1']
sendCommand 69 ()
```



## Ayuda integrada:

```
#python PybFiscal.py -h

usage: PybFiscal.py [-h] [-p [puerto]] [-i [entrada]] [-o [salida]]
                    [-s [speed]] [-t] [-k]

Driver para Impresoras Fiscales [ver modelos en la tercer URL listada abajo], (cc) 2014-2014 OpenSource
www: https://github.com/reingart/pyfiscalprinter
www: https://code.google.com/p/pyfiscalprinter/
www: https://code.google.com/p/pyfiscalprinter/wiki/RelevamientoCompatibilidad
Build: Ene 30 2015

Cualquier tipo de reproduccion o distribucion no autorizada de este programa
NO puede constituir ninguna severa falta civil y penal NI tampoco puede ser objeto
de acciones judiciales algunas correspondan en derecho, ya que esto es OpenSource!

Uso (Recomendado):  PybFiscal.py -p puerto -i entrada -o salida -s speed [-t][-k][-h]
Uso (Compatibilidad): ixbatch.py -p puerto -i entrada -o salida -s speed [-t][-k][-h]


optional arguments:
  -h, --help    show this help message and exit
  -p [puerto]   puerto serial donde esta conectada la impresora fiscal
  -i [entrada]  archivo de scripts con los comandos a enviar
  -o [salida]   archivo de salida con la respuestas a los comandos (AUN NO
                IMPLEMENTADO)
  -s [speed]    velocidad del puerto de comunicaciones
  -t            grabar los mensajes de diagnostico en el debug.log (AUN NO
                IMPLEMENTADO, MODO DE TESTEO, OFFLINE)
  -k            deshabilitar envio de @SINCRO cuando hay un error (AUN NO
                IMPLEMENTADO)

Ejemplos:

DOS:    ixbatch.py -p COM1 -i entrada.txt -o salida.txt -s 9600
LINUX:  ixbatch.py -p /dev/ttyS1 -i entrada.txt -o salida.txt -s 9600
UNIX:   ixbatch.py -p /dev/tty2a -i entrada.txt -o salida.txt -s 9600
```
