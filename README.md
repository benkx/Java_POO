## Principios de la programacion orientada a objetos (POO)


## Empleado por comision 3
```java
package empleadoporcomision;

public class EmpleadoPorComision3 {
    private String primerNombre;
    private String apellidoPaterno;
    private String numeroSeguroSocial;
    private double ventasBrutas; //ventas totales por semana
    private double tarifaComision; //porcentaje de comision
    
 //contructor con cinco argumentos
    public EmpleadoPorComision3(String nombre, String apellido, 
            String nss, double ventas, double tarifa )
    {
        primerNombre = nombre;
        apellidoPaterno = apellido;
        numeroSeguroSocial = nss;
        setVentasBrutas(ventas);
        setTarifaComision(tarifa);
        
    }
    public String getPrimerNombre() {
        return primerNombre;
    }

    public void setPrimerNombre(String primerNombre) {
        this.primerNombre = primerNombre;
    }

    public String getApellidoPaterno() {
        return apellidoPaterno;
    }

    public void setApellidoPaterno(String apellidoPaterno) {
        this.apellidoPaterno = apellidoPaterno;
    }

    public String getNumeroSeguroSocial() {
        return numeroSeguroSocial;
    }

    public void setNumeroSeguroSocial(String numeroSeguroSocial) {
        this.numeroSeguroSocial = numeroSeguroSocial;
    }

    public double getVentasBrutas() {
        return ventasBrutas;
    }

    public void setVentasBrutas(double ventas) {
        ventasBrutas =(ventas<0.0)?0.0:ventas;
    }

    public double getTarifaComision() {
        return tarifaComision;
    }

    public void setTarifaComision(double tarifa) {
        tarifaComision = (tarifa >0.0 && tarifa < 50.0)?tarifa:0.0;
    }
    
   //calcula los ingrsos
    public double ingreso()
    {
        return getTarifaComision() * getVentasBrutas();
    }
    
    //metodo
    //Devuelve representacion String del objeto EmpleadoComision3
    @Override
    public String toString()
    {
             return String.format("%s: %s %s\n%s: %s\n%s: %.2f\n%s: %.2f ", 
            "empleado por comision", getPrimerNombre(), getApellidoPaterno(),
            "numero de seguro social", getNumeroSeguroSocial(),
            "ventas bruta", getVentasBrutas(),
            "tarifa de comision", getTarifaComision());
    }
}
```
### Empleado base mas comision

```java
package empleadoporcomision;


public class EmpleadoBaseMasComision4 extends EmpleadoPorComision3 {

    private double salarioBase; //Salario base 

    public EmpleadoBaseMasComision4(String nombre, String apellido,
            String nss, double ventas, double tarifa, double salario) {
        super(nombre, apellido, nss, ventas, tarifa);

        setSalarioBase(salario); //Valida y almacena el salrio base
    }

    public double getSalarioBase() {
        return salarioBase;
    }

    public void setSalarioBase(double salario) {
        salarioBase = (salario < 0.0) ? 0.0 : salario;
    }

    @Override
    public double ingreso() {
        return getSalarioBase() + super.ingreso();
    }

    @Override
     public String toString()
    {
       
        return String.format("%s %s\n%s: %.2f" , 
                "con sueldo base", super.toString(), "Sueldo base", getSalarioBase());
    }
}
```

## Desplegando la Aplicacion

```java
public class EmpleadoPorComision {

    
    public static void main(String[] args) {
        //Crea instacia de un obejeto EmpleadoBaseMasComision4
        
        EmpleadoBaseMasComision4 empleado  = new 
        EmpleadoBaseMasComision4("Bob", "Marly", "222-222", 4440, 40, 3000);
        //Asignamos la referencia a la superclase de una varriable de la superclase
        EmpleadoPorComision3 emplePorComision = 
                new EmpleadoPorComision3("Juan", "Jose",  "123-3231", 1200, 87609);
//                
//       //invoca a toString en un objeto de la subclase, usuando una variable de la superclase
//        EmpleadoPorComision3 emplePorComision2 = empleado;
//        System.out.printf("%s %s: \n\n%s\n",
//                "Llamando a toString de EmpleadoBaseComision con"
//                        +" referencia de superclase",
//                "a un objeteo de la subclase", emplePorComision2.toString());
//                

        //Obtenemos datos del empleado por comision con sueldo base
        System.out.println("Informacion del empleado obtenido por los metodos establecer: \n");
        System.out.printf("%s %s\n", "El primer nombre es: ", empleado.getPrimerNombre());
        System.out.printf("%s %s\n", "El Apellido es: ", empleado.getApellidoPaterno());
        System.out.printf("%s %s\n", "El Numero de seguro social es: ", empleado.getNumeroSeguroSocial());
        System.out.printf("%s %s\n", "Venta:", empleado.getVentasBrutas());
        System.out.printf("%s %s\n", "Tarifa: ", empleado.getTarifaComision());
        System.out.printf("%s %s\n", "Salario base: ", empleado.getSalarioBase());
        
        empleado.setSalarioBase(200000);//establece el salario
        System.out.printf("%s %s\n", "Informacion actualizada del empleado obtenido por el ToString", empleado.toString());
    }
    
}
```
