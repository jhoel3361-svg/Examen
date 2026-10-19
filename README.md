Ejercicio 1
import 'dart:io';

// 1. Clase Estudiante
class Estudiante {
  String nombre;
  double sumaNotas;
  int cantidadNotas;

  // Constructor directo que recibe la suma acumulada
  Estudiante(this.nombre, this.sumaNotas, this.cantidadNotas);

  // Método 1: Calcula el promedio usando la suma acumulada
  double calcularPromedio() {
    return sumaNotas / cantidadNotas;
  }

  // Método 2: Determina el estado
  String determinarEstado() {
    if (calcularPromedio() >= 13) {
      return "Aprobado";
    } else {
      return "Desaprobado";
    }
  }

  // Método 3: Muestra el reporte
  void mostrarReporte() {
    print("\n----- REPORTE DEL ESTUDIANTE -----");
    print("Estudiante : $nombre");
    print("Promedio   : ${calcularPromedio().toStringAsFixed(2)}");
    print("Estado     : ${determinarEstado()}");
    print("----------------------------------");
  }
}

void main() {
  int nNota = 3;
  double suma = 0; // Se inicializa la variable acumuladora en 0

  stdout.write("Ingrese el nombre del estudiante: ");
  String nom = stdin.readLineSync() ?? "";

  // Bucle 'for' acumulando las notas con 'suma += nota'
  for (int i = 1; i <= nNota; i++) {
    stdout.write("Ingrese Nota $i: ");
    double nota = double.parse(stdin.readLineSync() ?? "0");
    suma += nota; // Suma acumulativa
  }

  // Se crea la instancia pasándole la suma final y la cantidad de notas
  Estudiante e = Estudiante(nom, suma, nNota);

  // Se llama al método para mostrar el resultado
  e.mostrarReporte();
}
Ejercicio 2
import 'dart:io';

// 1. Clase Producto con sus atributos obligatorios
class Producto {
  String nombre;
  double precioUnitario;
  int cantidadDisponible;

  // Constructor directo
  Producto(this.nombre, this.precioUnitario, this.cantidadDisponible);

  // Método 1: Calcular valor total del inventario
  double calcularValorInventario() {
    return precioUnitario * cantidadDisponible;
  }

  // Método 2: Determinar el estado del stock usando if, else if, else
  String determinarEstadoStock() {
    if (cantidadDisponible == 0) {
      return "Stock agotado";
    } else if (cantidadDisponible >= 1 && cantidadDisponible <= 5) {
      return "Stock bajo";
    } else {
      return "Stock suficiente";
    }
  }

  // Método 3: Mostrar la información completa del producto
  void mostrarInformacion() {
    print("\n----- INFORMACIÓN DEL PRODUCTO -----");
    print("Nombre            : $nombre");
    print("Precio Unitario   : S/ ${precioUnitario.toStringAsFixed(2)}");
    print("Cantidad          : $cantidadDisponible unidades");
    print("Valor Inventario  : S/ ${calcularValorInventario().toStringAsFixed(2)}");
    print("Estado del Stock  : ${determinarEstadoStock()}");
    print("-----------------------------------");
  }
}

void main() {
  print("=== REGISTRO DE PRODUCTO ===");

  // Lectura del nombre
  stdout.write("Ingrese el nombre del producto: ");
  String nombre = stdin.readLineSync() ?? "";

  // Lectura y validación del precio unitario (Condición 1: mayor que 0)
  double precio = 0;
  do {
    stdout.write("Ingrese el precio unitario (> 0): ");
    precio = double.parse(stdin.readLineSync() ?? "0");
    if (precio <= 0) {
      print(" Error: El precio debe ser mayor que cero.");
    }
  } while (precio <= 0);

  // Lectura y validación de la cantidad (Condición 2: mayor o igual a 0)
  int cantidad = -1;
  do {
    stdout.write("Ingrese la cantidad disponible (>= 0): ");
    cantidad = int.parse(stdin.readLineSync() ?? "-1");
    if (cantidad < 0) {
      print(" Error: La cantidad no puede ser negativa.");
    }
  } while (cantidad < 0);

  // Instancia de la clase (Condición 4)
  Producto producto1 = Producto(nombre, precio, cantidad);

  // Ejecución del método desde main()
  producto1.mostrarInformacion();
}
Ejercicio 3
import 'dart:io';

// 1. Clase Vendedor con sus atributos
class Vendedor {
  String nombre;
  double totalVentas;

  // Constructor directo
  Vendedor(this.nombre, this.totalVentas);

  // Método 1: Calcular la comisión según el monto de ventas
  double calcularComision() {
    if (totalVentas >= 2000) {
      return totalVentas * 0.10; // 10% de comisión
    } else {
      return totalVentas * 0.05; // 5% de comisión
    }
  }

  // Método 2: Mostrar el reporte del vendedor
  void mostrarReporte() {
    print("\n----- REPORTE DEL VENDEDOR -----");
    print("Vendedor         : $nombre");
    print("Monto de Ventas  : S/ ${totalVentas.toStringAsFixed(2)}");
    print("Comisión Ganada  : S/ ${calcularComision().toStringAsFixed(2)}");
    print("--------------------------------");
  }
}

void main() {
  print("=== REGISTRO DE VENDEDOR ===");

  // Lectura del nombre por teclado
  stdout.write("Ingrese el nombre del vendedor: ");
  String nombre = stdin.readLineSync() ?? "";

  // Lectura y validación del total de ventas (debe ser positivo)
  double ventas = 0;
  do {
    stdout.write("Ingrese el monto total de ventas: ");
    ventas = double.parse(stdin.readLineSync() ?? "0");
    if (ventas < 0) {
      print(" Error: El monto de ventas no puede ser negativo.");
    }
  } while (ventas < 0);

  // Instancia de la clase Vendedor
  Vendedor vendedor1 = Vendedor(nombre, ventas);

  // Ejecución de sus métodos desde main()
  vendedor1.mostrarReporte();
}
Ejercicio 4
import 'dart:io';

// 1. Clase RegistroTemperaturas
class RegistroTemperaturas {
  List<double> temperaturas = []; // Lista para guardar las 5 temperaturas

  // Método 1: Solicita las temperaturas de los 5 días por consola
  void registrarTemperaturas() {
    print("=== REGISTRO DE TEMPERATURAS DE LA CIUDAD ===");
    for (int i = 1; i <= 5; i++) {
      stdout.write("Ingrese la temperatura del día $i (°C): ");
      double temp = double.parse(stdin.readLineSync() ?? "0");
      temperaturas.add(temp);
    }
  }

  // Método 2: Calcula el promedio de las temperaturas
  double calcularPromedio() {
    double suma = 0;
    for (double temp in temperaturas) {
      suma += temp;
    }
    return suma / temperaturas.length;
  }

  // Método 3: Cuenta cuántos días superaron los 30 °C
  int contarDiasCalurosos() {
    int contador = 0;
    for (double temp in temperaturas) {
      if (temp > 30) {
        contador++;
      }
    }
    return contador;
  }

  // Método 4: Muestra el reporte final
  void mostrarReporte() {
    print("\n----- REPORTE CLIMÁTICO -----");
    print("Promedio semanal       : ${calcularPromedio().toStringAsFixed(2)} °C");
    print("Días calurosos (>30°C) : ${contarDiasCalurosos()} días");
    print("----------------------------");
  }
}

void main() {
  // 1. Crear una instancia de la clase
  RegistroTemperaturas registro = RegistroTemperaturas();

  // 2. Ejecutar sus métodos en orden desde main()
  registro.registrarTemperaturas();
  registro.mostrarReporte();
}
