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
