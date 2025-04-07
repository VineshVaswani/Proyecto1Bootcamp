Algoritmo Proyecto1_v2
	//Definir Descuentos, Impuestos
	Definir IVA, Descuento_10, Descuento_15, Descuento_20 Como Real
	IVA <- 0.19
	Descuento_10 = 0.1
	Descuento_15 = 0.15
	Descuento_20 = 0.2
	
	//definir variables del producto
	Definir precioUnitario, cantidad, tieneCupon, descuentoCupon, porcentajeCupon, montoCupon, porcentajeDescuento, descuentoCantidad, descuentoTotal, subtotal, totalIVA, totalPagar Como Real
	
	//Solicitar datos al comprador
	Escribir "Ingrese el precio del producto"
	Leer precioUnitario
	Escribir "Ingrese la cantidad de articulos"
	Leer cantidad
	Escribir "¿Tiene cúpon de descuento? (0:No, 1:Sí)"
	Leer tieneCupon
	
	
	Si tieneCupon = 1 Entonces
		Escribir "Ingrese el monto del cupón en %: "
		Leer montoCupon
		descuentoCupon <- precioUnitario * cantidad * (montoCupon/100)
		porcentajeCupon <- montoCupon
	Sino descuentoCupon = 0
		porcentajeCupon <- 0
	FinSi
	
	
	Si cantidad >= 20 Entonces
		descuentoCantidad = Descuento_20 * precioUnitario * cantidad
		porcentajeDescuento <- 20
	Sino si cantidad >= 15 Entonces
		descuentoCantidad = Descuento_15 * precioUnitario * cantidad
		porcentajeDescuento <- 15
	Sino si cantidad >= 10 Entonces
		descuentoCantidad = Descuento_10 * precioUnitario * cantidad
		porcentajeDescuento <- 10
	Sino descuentoCantidad = 0
		porcentajeDescuento <- 0
	FinSi
	FinSi
	FinSi
	
	//Envío
	Definir opcionZona Como Entero
	Definir peso, costoEnvio Como Real
	Definir zonasEnvio Como Caracter
	Dimension zonasEnvio[3] 
	zonasEnvio[1] <- "Región Metropolitana"
	zonasEnvio[2] <- "V Región"
	zonasEnvio[3] <- "IV Región"
	
	Escribir "Indique el peso de los productos adquiridos en KG: "
	Leer peso
	
	Escribir "Seleccione la zona de envío: "
	Para i <- 1 Hasta 3 Hacer
		Escribir i, ". ", zonasEnvio[i]
	FinPara
	Leer opcionZona
	
	
	Segun opcionZona Hacer
		Caso 1:
			costoEnvio <- 500 + peso * 1000
		Caso 2:
			costoEnvio <- 1000 + peso * 1500
		Caso 3:
			costoEnvio <- 750 + peso * 1200
	FinSegun
	
	descuentoTotal <- descuentoCantidad + descuentoCupon
	subtotal <- precioUnitario * cantidad - descuentoTotal
	totalIVA <- IVA * subtotal
	totalPagar <- costoEnvio + totalIVA + subtotal
	
	Escribir "Detalle de compra"
	Escribir "Tu descuento de cupon es de :", montoCupon, "%"
	Escribir "Tu descuento por cantidad es de :", porcentajeDescuento, "%"
	Escribir "Tu descuento total aplicado :", montoCupon + porcentajeDescuento, "%"
	Escribir "Total descontado en dinero $: ", descuentoTotal
	Escribir "El subtotal es: ", subtotal
	Escribir "El IVA de esta compra es de: ", IVA * subtotal
	Escribir "El costo del envio de la empresa de 3ros (IVA INCLUIDO) es de: ", costoEnvio
	Escribir "El total a pagar es de: ", totalPagar
	
FinAlgoritmo
