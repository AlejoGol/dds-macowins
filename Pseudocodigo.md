```java
class Prenda {
    var precioPropio;
    var estado;

    method precioDeVenta() {
        return estado.modificador(precioPropio);
    }
}

class Nueva {
    method modificador(precioPrenda) {
        return precioPrenda;
    }
}

class Promocion {
    var valorFijoDescontado;

    method modificador(precioPrenda) {
        return precioPrenda - valorFijoDescontado;
    }
}

class Liquidacion {
    method modificador(precioPrenda) {
        return precioPrenda * 0.5;
    }
}


class Venta {
    var fecha;
    var prendasVendidas = [];
    var formaDePago;

    method ganancia() {
        return formaDePago.ganancia(prendasVendidas);
    }
}

class PrendaVendida {
    var cantidad;
    var prenda;

    method costo() {
        return prenda.precioDeVenta() * cantidad;
    }
}

class Efectivo {
    method ganancia(prendasVendidas) {
        return prendasVendidas.sum(prendaVendida -> prendaVendida.costo());
    }
}

class Tarjeta {
    var cantidadDeCuotas;
    var coeficienteFijo;

    method ganancia(prendasVendidas) {
        var efectivo = new Efectivo();
        return efectivo.ganancia(prendasVendidas) cantidadDeCuotas * coeficienteFijo + prendasVendidas.sum(prendaVendida -> prendaVendida.costo() * 0.01);
    }
}


class Macowins {
    var ventas;

    method gananciaDeDia(fecha) {
        return ventas.filter(venta -> venta.fecha().equals(fecha)).sum(venta -> venta.ganancia());
    }
}
```