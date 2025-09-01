# 🛒 TecnoStore S.A.S – Sistema de Inventario Inteligente

**TecnoStore S.A.S** es una solución de software desarrollada en **Java (NetBeans IDE)** con **MySQL**, diseñada para **automatizar la gestión de inventarios en tiendas tecnológicas**.  

El proyecto integra principios de **ingeniería de software**, modelado **UML** y estándares de calidad **ISO/IEC 25010**, garantizando un sistema **eficiente, escalable y confiable** para procesos críticos como inventarios, ventas, compras y atención al cliente.  

---

## 📌 Badges del Proyecto
![Java](https://img.shields.io/badge/Java-8%2B-007396?style=for-the-badge&logo=openjdk&logoColor=white)  
![MySQL](https://img.shields.io/badge/MySQL-5.7%2B-4479A1?style=for-the-badge&logo=mysql&logoColor=white)  
![NetBeans](https://img.shields.io/badge/NetBeans-IDE-1B6AC6?style=for-the-badge&logo=apachenetbeanside&logoColor=white)  
![PMD](https://img.shields.io/badge/PMD-7.16.0-3C9DC5?style=for-the-badge&logo=codefactor&logoColor=white)  
![ISO/IEC 25010](https://img.shields.io/badge/ISO%2FIEC-25010-4CAF50?style=for-the-badge&logo=leaflet&logoColor=white)  



---

## 🎯 Objetivos del Proyecto
- **Automatizar** el control de inventarios (entradas, salidas y actualizaciones en tiempo real).  
- **Centralizar** la información de productos, clientes y proveedores.  
- **Optimizar** procesos de ventas, compras, devoluciones y facturación electrónica.  
- **Generar reportes inteligentes**: ventas por período, rotación de inventario, alertas de stock mínimo.  
- **Cumplir estándares de calidad** ISO/IEC 25010, garantizando funcionalidad, fiabilidad, usabilidad y mantenibilidad.  

---

## 🚀 Funcionalidades Clave
- **Gestión de Inventario**: registro de productos, control de stock, alertas automáticas y etiquetas con código de barras.  
- **Módulo de Ventas**: facturación electrónica, presupuestos configurables y devoluciones con actualización automática.  
- **Módulo de Compras y Proveedores**: órdenes de compra, recepción de mercancía, pagos y devoluciones.  
- **Gestión de Clientes**: información completa, presupuestos y seguimiento de historial de compras.  
- **Reportes Estadísticos**: análisis de ventas, productos más vendidos, proyecciones de demanda y cuentas por cobrar/pagar.  
- **Seguridad y Control de Acceso**: autenticación de usuarios y permisos diferenciados (Gerente / Vendedor).  

---

## 📊 Requisitos Funcionales y No Funcionales
✔ **Funcionales**:  
- Registro de productos con código, marca, modelo, precios y stock mínimo.  
- Registro de ventas con facturación y actualización de inventario.  
- Procesamiento de devoluciones y presupuestos configurables.  
- Gestión de clientes y proveedores.  
- Reportes automáticos (ventas, más vendidos, análisis de proveedores).  
- Control de acceso con roles de usuario.  

✔ **No Funcionales**:  
- Tiempo de respuesta < **2 segundos** en consultas de inventario.  
- Interfaz intuitiva con curva de aprendizaje < **4 horas**.  
- Compatibilidad: **Windows 10/11**, con mínimo **4 GB RAM**.  
- Escalabilidad: hasta **50.000 productos** y **10.000 transacciones diarias**.  
- Copias de seguridad automáticas y trazabilidad de operaciones.  
- Código modular con comentarios > **80% de cobertura**.  

---

## 🛠️ Tecnologías Utilizadas
- **Lenguaje:** Java (NetBeans IDE)  
- **Base de Datos:** MySQL  
- **Modelado:** UML (casos de uso, actividades, clases, modelo lógico–relacional)  
- **Gestión de calidad:** ISO/IEC 25010 – ISO/IEC 25000  
- **Control de código:** GitHub  
- **Pruebas internas:** PMD 7.16.0   

---

## 📈 Beneficios del Sistema
- Reducción de errores humanos en la gestión de inventarios.  
- Procesos más rápidos y trazables.  
- Información confiable y en tiempo real para decisiones estratégicas.  
- Seguridad reforzada con control de roles y respaldos automáticos.  
- Escalabilidad y adaptabilidad al crecimiento del negocio.  

---

## 🔍 Estándares y Buenas Prácticas
- **ISO/IEC 25010**: evaluación de la calidad del software.  
- **ISO/IEC 25000**: marco de referencia de calidad.  
- **Buenas prácticas de programación en Java**: modularidad, comentarios y trazabilidad de requisitos.  
- **Uso de UML**: trazabilidad entre requisitos, diseño y modelo de datos.  
- **Normativa de facturación electrónica**: cumplimiento legal en el módulo de ventas.  

---
## 🗄️ Esquema Relacional en MySQL – TecnoStore S.A.S (MySQL Workbench)

```MySQL
-- ============================================================
-- 🛒 TecnoStore S.A.S – Script de Creación de Base de Datos
-- Autor: Wily Duvan Villamil Rey
-- Fecha: Agosto 2025
-- Descripción: Definición del esquema relacional del sistema
-- ============================================================

-- ================================
-- CREACIÓN DE BASE DE DATOS
-- ================================
CREATE DATABASE IF NOT EXISTS tecnostore;
USE tecnostore;
```
![Modelo de Base de Datos](https://drive.google.com/uc?export=view&id=15dMDEkXKKx5TAV9G3gtWEuiuY71Nv-XY)

---

```MySQL
-- ================================
-- TABLA: Proveedor
-- ================================
CREATE TABLE Proveedor (
    id_proveedor INT AUTO_INCREMENT PRIMARY KEY,
    nombre       VARCHAR(100) NOT NULL,
    contacto     VARCHAR(100),
    direccion    VARCHAR(150)
);
```
![Tabla Proveedor](https://drive.google.com/uc?export=view&id=1Rr6YLSIJe8mYAD6QntmOXKvd1jlysK2R)

---

```MySQL
-- ================================
-- TABLA: Entrada_Producto
-- ================================
CREATE TABLE Entrada_Producto (
    id_entrada     INT AUTO_INCREMENT PRIMARY KEY,
    fecha          DATE NOT NULL,
    cantidad       INT NOT NULL,
    detalle_entrada VARCHAR(255),
    id_proveedor   INT,
    FOREIGN KEY (id_proveedor) REFERENCES Proveedor(id_proveedor)
);
```
![Tabla Entrada Producto](https://drive.google.com/uc?export=view&id=1l0e2Ch4hhD_hf8NjZ4_bIvPzUZ1CVh9D)

---

```MySQL
-- ================================
-- TABLA: Producto
-- ================================
CREATE TABLE Producto (
    id_producto    INT AUTO_INCREMENT PRIMARY KEY,
    codigo_interno VARCHAR(50) UNIQUE NOT NULL,
    descripcion    VARCHAR(200),
    marca          VARCHAR(100),
    modelo         VARCHAR(100),
    precio         DECIMAL(10,2) NOT NULL,
    stock          INT DEFAULT 0
);
```
![Tabla Producto](https://drive.google.com/uc?export=view&id=1aQhkJL7aptzaHXKfj506kww0xCjpZMKX)

---

```MySQL
-- ================================
-- TABLA: Cliente
-- ================================
CREATE TABLE Cliente (
    id_cliente INT AUTO_INCREMENT PRIMARY KEY,
    nombre     VARCHAR(100) NOT NULL,
    correo     VARCHAR(100) UNIQUE,
    telefono   VARCHAR(20)
);
```
![Tabla Cliente](https://drive.google.com/uc?export=view&id=12_rK6EggzsH3eoYkA5LJCblw-BDGmIKH)

---

```MySQL
-- ================================
-- TABLA: Presupuesto
-- ================================
CREATE TABLE Presupuesto (
    id_presupuesto INT AUTO_INCREMENT PRIMARY KEY,
    fecha          DATE NOT NULL,
    validez        DATE,
    total_estimado DECIMAL(12,2),
    id_cliente     INT,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente)
);
```
![Tabla Presupuesto](https://drive.google.com/uc?export=view&id=1CE7IKZ-eqVwymusfDxy8juUBHcMHDVKq)

----

```MySQL
-- ================================
-- TABLA: Detalle_Presupuesto
-- ================================
CREATE TABLE Detalle_Presupuesto (
    id_detalle     INT AUTO_INCREMENT PRIMARY KEY,
    cantidad       INT NOT NULL,
    precio_estimado DECIMAL(10,2) NOT NULL,
    id_presupuesto INT,
    id_producto    INT,
    FOREIGN KEY (id_presupuesto) REFERENCES Presupuesto(id_presupuesto),
    FOREIGN KEY (id_producto) REFERENCES Producto(id_producto)
);
```
![Tabla Detalle Presupuesto](https://drive.google.com/uc?export=view&id=1ad0oyB7B252n45paRA667BsK8kFrXNL-)

---
```MySQL
-- ================================
-- TABLA: Usuario
-- ================================
CREATE TABLE Usuario (
    id_usuario  INT AUTO_INCREMENT PRIMARY KEY,
    nombre      VARCHAR(100) NOT NULL,
    correo      VARCHAR(100) UNIQUE NOT NULL,
    contrasena  VARCHAR(255) NOT NULL
);
```
![Tabla Usuario](https://drive.google.com/uc?export=view&id=1dpZUI5JgT1bJPSyWQSug9KrPZm1-aiha)

---
```MySQL
-- ================================
-- TABLA: Venta
-- ================================
CREATE TABLE Venta (
    id_venta   INT AUTO_INCREMENT PRIMARY KEY,
    estado     VARCHAR(50) NOT NULL,
    fecha      DATE NOT NULL,
    id_cliente INT,
    id_usuario INT,
    FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente),
    FOREIGN KEY (id_usuario) REFERENCES Usuario(id_usuario)
);
```
![Tabla Venta](https://drive.google.com/uc?export=view&id=1cwAa0Y9Kmm6HabNz5vs5mcW--ifuKAJw)

---
```MySQL
-- ================================
-- TABLA: Detalle_Venta
-- ================================
CREATE TABLE Detalle_Venta (
    id_detalle     INT AUTO_INCREMENT PRIMARY KEY,
    cantidad       INT NOT NULL,
    precio_unitario DECIMAL(10,2) NOT NULL,
    id_venta       INT,
    id_producto    INT,
    FOREIGN KEY (id_venta) REFERENCES Venta(id_venta),
    FOREIGN KEY (id_producto) REFERENCES Producto(id_producto)
);
```
![Tabla Detalle Venta](https://drive.google.com/uc?export=view&id=1STcXK8vNOTH2I598uP5J4rAn2puWGaK-)

---
```MySQL
-- ================================
-- TABLA: Devolucion
-- ================================
CREATE TABLE Devolucion (
    id_devolucion   INT AUTO_INCREMENT PRIMARY KEY,
    fecha           DATE NOT NULL,
    id_detalle_venta INT,
    cantidad        INT NOT NULL,
    motivo          VARCHAR(255),
    estado          VARCHAR(50),
    FOREIGN KEY (id_detalle_venta) REFERENCES Detalle_Venta(id_detalle)
);

-- ============================================================
-- ✅ Fin del Script 
-- ============================================================
```
![Tabla Devolución](https://drive.google.com/uc?export=view&id=1oIiU48tCBGUqgKYIuaG4G9Dg6IwRY4r0)

---
## 🛠️☕ Implementación en Java con NetBeans IDE
---

![Vista General](https://drive.google.com/uc?export=view&id=1HhigkQeJCbu7xWpB6nWcM0zlMerf9xfB)

---
*Vista Detalle Cliente*

![Vista Detalle Cliente](https://drive.google.com/uc?export=view&id=1BS3uO_5ul9wKAIONa-2rTxGK5602zzZ4)
*Prueba de inserción de datos desde NetBeans hacia la base de datos, mostrando la tabla detalle_cliente.*

---


## 1. 🔌 Conexión a la Base de Datos

El sistema incluye una clase dedicada para la **conexión a MySQL** mediante JDBC.  
Esto centraliza la configuración y permite mantener el código modular y reutilizable.

### Clase `ConexionBD.java`:

```java
package ConexionBD;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

/**
 * Clase encargada de establecer la conexión con la base de datos MySQL
 * para el sistema TecnoStore S.A.S.
 *
 * Esta implementación sigue principios de modularidad y reutilización,
 * permitiendo centralizar la lógica de conexión y facilitar el mantenimiento.
 *
 * Autor: Wily Duvan Villamil Rey 
 * Fecha: Agosto 2025
 */
public class ConexionBD {

    // ================================
    // 🔧 Parámetros de configuración
    // ================================
    private static final String URL = "jdbc:mysql://localhost:3306/tecnostore"
                                    + "?useSSL=false"
                                    + "&allowPublicKeyRetrieval=true"
                                    + "&serverTimezone=UTC";
    private static final String USER = "Usuario de Conexion Base de Datos";
    private static final String PASSWORD = "Contraseña de Acceso";

    // ============================================
    // 🔌 Método para establecer la conexión JDBC
    // ============================================
    public static Connection conectar() {
        Connection conexion = null;

        try {
            // Cargar el driver JDBC de MySQL
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Intentar establecer la conexión
            conexion = DriverManager.getConnection(URL, USER, PASSWORD);
            System.out.println("✅ Conexión exitosa a la base de datos.");

        } catch (ClassNotFoundException e) {
            System.out.println("❌ Error: No se encontró el driver JDBC de MySQL.");
            e.printStackTrace();

        } catch (SQLException e) {
            System.out.println("❌ Error al conectar a la base de datos.");
            System.out.println("📌 Verifica que el servidor esté activo y que las credenciales sean correctas.");
            e.printStackTrace();
        }

        return conexion;
    }
}
```

---
## 2. 📂 Clase Modelo – Entidad Usuario

El **modelo** representa las entidades del sistema y mantiene la trazabilidad con el modelo lógico–relacional definido en la base de datos.  
En este caso, la clase `Usuario` encapsula los atributos y comportamientos asociados a los usuarios del sistema:

```java
package modelo;

/**
 * Clase que representa un usuario del sistema TecnoStore S.A.S.
 * Esta clase encapsula los atributos definidos en el modelo lógico relacional
 * y permite su trazabilidad dentro del sistema.
 *
 * Cumple con principios de diseño orientado a objetos, trazabilidad de datos,
 * y se alinea con los estándares de calidad ISO/IEC 25010.
 *
 * Autor: Wily Duvan Villamil Rey
 * Fecha: Agosto 2025
 */
public class Usuario {

    // Atributos según el modelo lógico relacional
    private int idUsuario;       // Clave primaria
    private String nombre;       // Nombre del usuario
    private String correo;       // Correo electrónico
    private String contrasena;   // Contraseña (idealmente encriptada)

    // Constructor vacío
    public Usuario() {}

    // Constructor completo
    public Usuario(int idUsuario, String nombre, String correo, String contrasena) {
        this.idUsuario = idUsuario;
        this.nombre = nombre;
        this.correo = correo;
        this.contrasena = contrasena;
    }

    // Getters y Setters
    public int getIdUsuario() {
        return idUsuario;
    }

    public void setIdUsuario(int idUsuario) {
        this.idUsuario = idUsuario;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getCorreo() {
        return correo;
    }

    public void setCorreo(String correo) {
        this.correo = correo;
    }

    public String getContrasena() {
        return contrasena;
    }

    public void setContrasena(String contrasena) {
        this.contrasena = contrasena;
    }

    // Método toString
    @Override
    public String toString() {
        return "Usuario{" +
                "idUsuario=" + idUsuario +
                ", nombre='" + nombre + '\'' +
                ", correo='" + correo + '\'' +
                ", contrasena='" + contrasena + '\'' +
                '}';
    }
}
```

---
## 3. 📂  DAO – Acceso a Datos (CRUD de Usuario)

El sistema implementa el patrón **DAO (Data Access Object)** para aislar la lógica de acceso a datos de la lógica de negocio, promoviendo **modularidad, mantenibilidad** y cumpliendo con estándares de calidad **ISO/IEC 25010**.

A continuación, la clase **UsuarioDAO** encargada de la gestión CRUD:

```java
package dao;

import modelo.Usuario;
import ConexionBD.ConexionBD;
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Clase DAO para gestionar operaciones CRUD sobre la entidad Usuario.
 *
 * Autor: Wily Duvan Villamil Rey 
 * Fecha: Agosto 2025
 */
public class UsuarioDAO {

    // 🔒 Conexión inmutable con la base de datos
    private final Connection conn;

    public UsuarioDAO() {
        this.conn = ConexionBD.conectar();
    }

    // Registrar nuevo usuario
    public boolean registrarUsuario(Usuario usuario) {
        final String sql = "INSERT INTO Usuario (nombre, correo, contrasena) VALUES (?, ?, ?)";
        try (PreparedStatement stmt = conn.prepareStatement(sql)) {
            stmt.setString(1, usuario.getNombre());
            stmt.setString(2, usuario.getCorreo());
            stmt.setString(3, usuario.getContrasena());
            stmt.executeUpdate();
            System.out.println("✅ Usuario registrado correctamente.");
            return true;
        } catch (SQLException e) {
            logError("registrarUsuario", e);
            return false;
        }
    }

    // Listar todos los usuarios
    public List<Usuario> listarUsuarios() {
        List<Usuario> lista = new ArrayList<>();
        final String sql = "SELECT * FROM Usuario";
        try (Statement stmt = conn.createStatement();
             ResultSet rs = stmt.executeQuery(sql)) {
            while (rs.next()) {
                Usuario u = new Usuario(
                    rs.getInt("idUsuario"),
                    rs.getString("nombre"),
                    rs.getString("correo"),
                    rs.getString("contrasena")
                );
                lista.add(u);
            }
        } catch (SQLException e) {
            logError("listarUsuarios", e);
        }
        return lista;
    }

    // Buscar usuario por ID
    public Usuario buscarPorId(int idUsuario) {
        final String sql = "SELECT * FROM Usuario WHERE idUsuario = ?";
        try (PreparedStatement stmt = conn.prepareStatement(sql)) {
            stmt.setInt(1, idUsuario);
            try (ResultSet rs = stmt.executeQuery()) {
                if (rs.next()) {
                    return new Usuario(
                        rs.getInt("idUsuario"),
                        rs.getString("nombre"),
                        rs.getString("correo"),
                        rs.getString("contrasena")
                    );
                }
            }
        } catch (SQLException e) {
            logError("buscarPorId", e);
        }
        return null;
    }

    // Buscar usuario por correo
    public Usuario buscarPorCorreo(String correo) {
        final String sql = "SELECT * FROM Usuario WHERE correo = ?";
        try (PreparedStatement stmt = conn.prepareStatement(sql)) {
            stmt.setString(1, correo);
            try (ResultSet rs = stmt.executeQuery()) {
                if (rs.next()) {
                    return new Usuario(
                        rs.getInt("idUsuario"),
                        rs.getString("nombre"),
                        rs.getString("correo"),
                        rs.getString("contrasena")
                    );
                }
            }
        } catch (SQLException e) {
            logError("buscarPorCorreo", e);
        }
        return null;
    }

    // Actualizar usuario
    public boolean actualizarUsuario(Usuario usuario) {
        final String sql = "UPDATE Usuario SET nombre = ?, correo = ?, contrasena = ? WHERE idUsuario = ?";
        try (PreparedStatement stmt = conn.prepareStatement(sql)) {
            stmt.setString(1, usuario.getNombre());
            stmt.setString(2, usuario.getCorreo());
            stmt.setString(3, usuario.getContrasena());
            stmt.setInt(4, usuario.getIdUsuario());
            stmt.executeUpdate();
            System.out.println("✅ Usuario actualizado correctamente.");
            return true;
        } catch (SQLException e) {
            logError("actualizarUsuario", e);
            return false;
        }
    }

    // Eliminar usuario
    public boolean eliminarUsuario(int idUsuario) {
        final String sql = "DELETE FROM Usuario WHERE idUsuario = ?";
        try (PreparedStatement stmt = conn.prepareStatement(sql)) {
            stmt.setInt(1, idUsuario);
            stmt.executeUpdate();
            System.out.println("✅ Usuario eliminado correctamente.");
            return true;
        } catch (SQLException e) {
            logError("eliminarUsuario", e);
            return false;
        }
    }

    // 🔒 Cerrar conexión manualmente
    public void cerrarConexion() {
        try {
            if (conn != null && !conn.isClosed()) {
                conn.close();
                System.out.println("🔒 Conexión cerrada correctamente.");
            }
        } catch (SQLException e) {
            logError("cerrarConexion", e);
        }
    }

    // Método privado para trazabilidad de errores
    private void logError(String metodo, SQLException e) {
        System.err.println("❌ Error en " + metodo + ": " + e.getMessage());
    }
}
```

---

## 4. 📂 Clase Controlador 

El proyecto implementa la arquitectura **Modelo – Vista – Controlador (MVC)**, lo que permite **separar responsabilidades**, mejorar la **mantenibilidad** y garantizar la **escalabilidad** del sistema.

```java
package controlador;

import dao.UsuarioDAO;
import modelo.Usuario;
import java.util.List;

/**
 * Controlador para gestionar la lógica de negocio relacionada con la entidad Usuario.
 * Actúa como intermediario entre la capa de presentación y la capa de acceso a datos.
 *
 * Cumple con principios SOLID, trazabilidad de datos, modularidad,
 * y estándares de calidad ISO/IEC 25010.
 *
 * Autor: Wily Duvan Villamil Rey 
 * Fecha: Agosto 2025
 */
public class UsuarioControlador {

    // 🔒 Dependencia inmutable al DAO
    private final UsuarioDAO usuarioDAO;

    public UsuarioControlador() {
        this.usuarioDAO = new UsuarioDAO();
    }

    // Registro de nuevo usuario
    public boolean registrarUsuario(String nombre, String correo, String contrasena) {
        Usuario usuario = new Usuario(0, nombre, correo, contrasena);
        return usuarioDAO.registrarUsuario(usuario);
    }

    // Búsqueda por ID
    public Usuario buscarPorId(int idUsuario) {
        return usuarioDAO.buscarPorId(idUsuario);
    }

    // Listado de usuarios
    public List<Usuario> listarUsuarios() {
        return usuarioDAO.listarUsuarios();
    }

    // Actualización de usuario
    public boolean actualizarUsuario(int idUsuario, String nombre, String correo, String contrasena) {
        Usuario usuario = new Usuario(idUsuario, nombre, correo, contrasena);
        return usuarioDAO.actualizarUsuario(usuario);
    }

    // Eliminación de usuario
    public boolean eliminarUsuario(int idUsuario) {
        return usuarioDAO.eliminarUsuario(idUsuario);
    }

    // Cierre de conexión
    public void cerrarConexion() {
        usuarioDAO.cerrarConexion();
    }
}
```

---
## 5. 🖥️ Vista – Interfaz por Consola

El sistema incluye una **vista por consola** que permite interactuar con el módulo **Detalle de Usuario**.  
Se pueden registrar, listar y consultar usuarios de manera sencilla, aplicando validaciones y estándares de calidad.

### La clase `VistaDetalleUsuarioConsola.java`:

```java
package vista;

import controlador.UsuarioControlador;
import modelo.Usuario;
import java.util.InputMismatchException;
import java.util.List;
import java.util.Scanner;

/**
 * Vista por consola para el módulo Detalle de Usuario del sistema TecnoStore S.A.S.
 * Permite registrar, listar y consultar usuarios del sistema.
 *
 * Aplica principios SOLID, trazabilidad, validación de entrada y estándares ISO/IEC 25010.
 *
 * Autor: Wily Duvan Villamil Rey 
 * Fecha: Agosto 2025
 */
public class VistaDetalleUsuarioConsola {

    public static final Scanner scanner = new Scanner(System.in);
    public static final UsuarioControlador controlador = new UsuarioControlador();

    public static void main(String[] args) {
        mostrarMenu();
        controlador.cerrarConexion();
    }

    public static void mostrarMenu() {
        int opcion;
        do {
            System.out.println("\n=== Módulo Detalle de Usuario ===");
            System.out.println("1. Registrar nuevo usuario");
            System.out.println("2. Listar todos los usuarios");
            System.out.println("3. Buscar usuario por ID");
            System.out.println("0. Salir");
            System.out.print("Seleccione una opción: ");

            try {
                opcion = scanner.nextInt();
                scanner.nextLine(); // Limpiar buffer
                switch (opcion) {
                    case 1 -> registrarUsuario();
                    case 2 -> listarUsuarios();
                    case 3 -> buscarPorId();
                    case 0 -> System.out.println("🔚 Saliendo del módulo...");
                    default -> System.out.println("⚠️ Opción inválida.");
                }
            } catch (InputMismatchException e) {
                System.out.println("⚠️ Entrada no válida. Ingrese un número.");
                scanner.nextLine();
                opcion = -1;
            }
        } while (opcion != 0);
    }

    // Registro de usuario
    public static void registrarUsuario() {
        try {
            System.out.println("\n--- Registro de Usuario ---");
            System.out.print("Nombre: ");
            String nombre = scanner.nextLine();

            System.out.print("Correo electrónico: ");
            String correo = scanner.nextLine();

            System.out.print("Contraseña: ");
            String contrasena = scanner.nextLine();

            boolean exito = controlador.registrarUsuario(nombre, correo, contrasena);
            System.out.println(exito ? "✅ Usuario registrado exitosamente." : "❌ Error al registrar el usuario.");
        } catch (InputMismatchException e) {
            System.out.println("⚠️ Entrada inválida. Verifique los datos.");
            scanner.nextLine();
        }
    }

    // Listado de usuarios
    public static void listarUsuarios() {
        System.out.println("\n--- Listado de Usuarios ---");
        List<Usuario> lista = controlador.listarUsuarios();
        if (lista.isEmpty()) {
            System.out.println("📭 No hay usuarios registrados.");
        } else {
            for (Usuario u : lista) {
                System.out.println(u.toString());
            }
        }
    }

    // Búsqueda por ID
    public static void buscarPorId() {
        try {
            System.out.print("\nIngrese el ID del usuario a buscar: ");
            int id = scanner.nextInt();
            scanner.nextLine();

            Usuario usuario = controlador.buscarPorId(id);
            if (usuario != null) {
                System.out.println("🔍 Usuario encontrado:");
                System.out.println(usuario.toString());
            } else {
                System.out.println("❌ No se encontró ningún usuario con ese ID.");
            }
        } catch (InputMismatchException e) {
            System.out.println("⚠️ Entrada inválida.");
            scanner.nextLine();
        }
    }
}
```
---
## 6. ▶️ Clase Principal `TecnoStoreSAS`

La clase `TecnoStoreSAS` es el **punto de arranque del sistema**, encargada de:  
- Establecer la conexión con la base de datos MySQL mediante `ConexionBD`.  
- Ejecutar una consulta simple (`SELECT NOW()`) para verificar conectividad.  
- Mostrar en consola la fecha/hora actual obtenida desde MySQL como prueba de funcionamiento.  

### Ejemplo de código:

```java
package tecnostore.s.a.s;

import ConexionBD.ConexionBD;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

public class TecnoStoreSAS {
    public static void main(String[] args) {
        Connection conn = ConexionBD.conectar();
        if (conn != null) {
            try {
                Statement stmt = conn.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT NOW() as fecha;");
                if (rs.next()) {
                    System.out.println("✅ Conexión OK - Fecha desde MySQL: " + rs.getString("fecha"));
                }
                conn.close();
            } catch (Exception e) {
                System.out.println("❌ Error al ejecutar la consulta.");
                e.printStackTrace();
            }
        } else {
            System.out.println("❌ No se pudo conectar a la base de datos.");
        }
    }
}
```
---
