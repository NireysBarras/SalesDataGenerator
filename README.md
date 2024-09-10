# SalesDataGenerator

# Generación de Archivos de Prueba en Java

Este repositorio contiene un programa Java diseñado para generar archivos de prueba que contienen información sobre vendedores, productos y ventas. El propósito es crear archivos de texto que simulen datos para propósitos de prueba o demostración.

## Estructura del Proyecto

El proyecto consta de una sola clase Java llamada `GenerateInfoFiles`. Esta clase incluye varios métodos para generar archivos de texto con datos simulados.

### Clase `GenerateInfoFiles`

La clase `GenerateInfoFiles` proporciona métodos estáticos para crear archivos de texto con datos simulados. La clase utiliza la biblioteca estándar de Java para manejar la escritura de archivos y la generación de números aleatorios.

#### Métodos

1. **`public static void main(String[] args)`**

   Este es el método principal que se ejecuta cuando se inicia el programa. Llama a los métodos de generación de archivos para crear archivos de prueba:

   - `createSalesMenFile(5, "Juan Pérez", 123456);`
   - `createProductsFile(10);`
   - `createSalesManInfoFile(5);`

   Muestra un mensaje de éxito o error en la consola.

2. **`public static void createSalesMenFile(int randomSalesCount, String name, long id) throws IOException`**

   Genera un archivo de texto con ventas simuladas para un vendedor específico. El archivo se nombra usando el formato `name_id.txt`, donde `name` es el nombre del vendedor y `id` es su identificador único.

   - **Parámetros:**
     - `randomSalesCount`: Número de ventas aleatorias a generar.
     - `name`: Nombre del vendedor.
     - `id`: ID del vendedor.

   El archivo contiene el ID del vendedor y una lista de ventas con productos y cantidades aleatorias.

3. **`public static void createProductsFile(int productsCount) throws IOException`**

   Crea un archivo llamado `products.txt` que contiene una lista de productos simulados.

   - **Parámetro:**
     - `productsCount`: Número de productos a generar.

   Cada línea del archivo contiene el identificador del producto, su nombre y un precio aleatorio.

4. **`public static void createSalesManInfoFile(int salesmanCount) throws IOException`**

   Genera un archivo llamado `salesmen.txt` con información simulada sobre los vendedores.

   - **Parámetro:**
     - `salesmanCount`: Número de vendedores a generar.

   El archivo contiene líneas con el ID del vendedor, nombre y apellido simulados.

# Dependencias
JDK 8 o superior.

# Codigo
````
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Random;

public class GenerateInfoFiles {

    private static final Random RANDOM = new Random();

    public static void main(String[] args) {
        try {
            // Genera archivos de prueba
            createSalesMenFile(5, "Juan Pérez", 123456);
            createProductsFile(10);
            createSalesManInfoFile(5);
            System.out.println("Archivos de prueba generados exitosamente.");
        } catch (IOException e) {
            System.err.println("Error al generar archivos de prueba: " + e.getMessage());
        }
    }

    /*
     *  randomSalesCount Cantidad de ventas a generar.
     *  name Nombre del vendedor.
     *  id ID del vendedor.
     */
    public static void createSalesMenFile(int randomSalesCount, String name, long id) throws IOException {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter(name + "_" + id + ".txt"))) {
            writer.write("DNI;" + id + "\n");
            for (int i = 0; i < randomSalesCount; i++) {
                writer.write("P" + (RANDOM.nextInt(10) + 1) + ";" + (RANDOM.nextInt(10) + 1) + ";\n");
            }
        }
    }

    /**
     * 
     * productsCount = Cantidad de productos a generar.
     */
    public static void createProductsFile(int productsCount) throws IOException {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("products.txt"))) {
            for (int i = 1; i <= productsCount; i++) {
                writer.write("P" + i + ";Producto" + i + ";" + (RANDOM.nextInt(100) + 1) + "\n");
            }
        }
    }

    /**
     *  salesmanCount Cantidad de vendedores a generar.
     */
    public static void createSalesManInfoFile(int salesmanCount) throws IOException {
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("salesmen.txt"))) {
            for (int i = 0; i < salesmanCount; i++) {
                writer.write("DNI;" + (100000 + i) + ";Nombre" + i + ";Apellido" + i + "\n");
            }
        }
    }
}
````
