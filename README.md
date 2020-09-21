## Principios de la programacion orientada a objetos (POO)


## Empleado por comision 3

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


