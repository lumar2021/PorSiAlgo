import java.util.*;
import java.io.*;

public class Administrador {

    private Scanner entrada = new Scanner(System.in);
    private String representanteLegal;
    private int cedulaRepresentante;
    private int telefono;
    private int nit;
    private String correoElectronico;
    private String nombreTienda;
    private int numeroLocal;
    private String contrasenia;

    public void registroAdministrador() {

        System.out.println("Representante Legal del local: ");
        this.representanteLegal = entrada.next();
        System.out.println("Cedula del Representante Legal: ");
        this.cedulaRepresentante = entrada.nextInt();
        System.out.println("Telefono de contacto: ");
        this.telefono = entrada.nextInt();
        System.out.println("NIT: ");
        this.nit = entrada.nextInt();
        System.out.println("Correo Electronico: ");
        this.correoElectronico = entrada.next();
        System.out.println("Nombre del negocio: ");
        this.nombreTienda = entrada.next();
        System.out.println("Numero del negocio(Local): ");
        this.numeroLocal = entrada.nextInt();
        String contra1;
        String contra2;

        System.out.println("Cree una contraseña: ");
        contra1 = entrada.next();

        while(true){
            System.out.println("Confirmar contraseña: ");
            contra2 = entrada.next();

            if(!(contra1.equals(contra2))){
                System.out.println("Las contraseñas no coinciden");
            }else{
                break;
            }
        }
        this.contrasenia = contra1;

        File archivo;
        FileWriter escribir;
        PrintWriter linea;
        archivo = new File("users.text");
        if(!archivo.exists()){
            try
            {
                archivo.createNewFile();
                this.telefono = 123;
                escribir = new FileWriter(archivo,true);
                linea = new PrintWriter(escribir);
                linea.print("Representantee"+this.representanteLegal+"Cedulaa"+this.cedulaRepresentante+"Telefonoo"+this.telefono+"nitt"+this.nit+
                    "correoo"+this.correoElectronico+"negocioo"+this.nombreTienda+"Numeroo"+this.numeroLocal+"contraa"+this.contrasenia+"\n");
                linea.close();
                escribir.close();
            }
            catch (IOException ioe)
            {
                ioe.printStackTrace();
            }
        }else{
            try
            {
                this.telefono = 123;
                escribir = new FileWriter(archivo,true);
                linea = new PrintWriter(escribir);
                linea.print("Representantee"+this.representanteLegal+"Cedulaa"+this.cedulaRepresentante+"Telefonoo"+this.telefono+"nitt"+this.nit+
                    "correoo"+this.correoElectronico+"negocioo"+this.nombreTienda+"Numeroo"+this.numeroLocal+"contraa"+this.contrasenia+"-----\n");
                linea.close();
                escribir.close();
            }
            catch (IOException ioe)
            {
                ioe.printStackTrace();
            }
        }
            System.out.println("Se ha registrado el usuario correctamente");
            this.inicioSesion();
    }

    public void inicioSesion() {
        File archivoLeer;
        FileReader lector;
        String stringTotal = "";
        archivoLeer = new File("users.text");
        String cadena = "";

        ArrayList<Integer> cedulas = new ArrayList<Integer>();
        ArrayList<String> contrasenias = new ArrayList<String>();

        try
        {
            lector = new FileReader("users.text");
            BufferedReader almacenamiento = new BufferedReader(lector);
            stringTotal="";
            while(stringTotal!=null){
                try{
                    stringTotal = almacenamiento.readLine();
                    if(stringTotal!=null){
                        cadena = cadena + stringTotal;
                    }
                }
                catch(IOException ioe)
                {
                    ioe.printStackTrace();
                }

            }

            try{
                almacenamiento.close();
                lector.close();
            }
            catch(IOException ioe)
            {
                ioe.printStackTrace();
            }

        }
        catch (IOException ioe)
        {
            ioe.printStackTrace();
        }

        int iniContra = 0;
        int finContra = 0;
        int iniCed = 0;
        int finCed = 0;

        for(int i = 0; i<cadena.length(); i++){
            iniCed = cadena.indexOf("Cedulaa", finCed);
            finCed = cadena.indexOf("Telefonoo", iniCed);

            iniContra = cadena.indexOf("contraa",iniCed);
            finContra = cadena.indexOf("-----",finCed);

            if(finCed == -1 || iniCed == -1 ){break;}
            if(iniContra == -1 || finContra == -1 ){break;}

            String verfCed = cadena.substring(iniCed+7, finCed);
            int intCedula = Integer.parseInt(verfCed);
            String verfContra = cadena.substring(iniContra+7, finContra);

            cedulas.add(intCedula);
            contrasenias.add(verfContra);
        }

        boolean verificacion = false;
        int intentos = 0;

        System.out.println("Ingrese cedula");
        int comproCed = entrada.nextInt();
        System.out.println(comproCed);
        String comproContra="";
        int posicion = -1;

        while (verificacion != true && intentos<5) {
            for(int i = 0; i<cedulas.size();i++){
                if(cedulas.get(i) == comproCed){
                    posicion=i;
                }else if(((this.contrasenia!=null) && (this.contrasenia.equals(comproContra)))){
                    posicion=0;
                }
            }
            if(posicion<0){
                System.out.println("No se ha encontrado la cedula ingresada");
                this.inicioSesion();
                break;
            }
            System.out.println("Ingresa la contraseña");
            comproContra = entrada.next();

            if(contrasenias.get(posicion).equals(comproContra) || (((this.contrasenia!=null) && (this.contrasenia.equals(comproContra))))){
                System.out.println("Ha iniciado sesión correctamente");
                verificacion = true;
            }
            else{
                System.out.println("La contraseña es incorrecta");
                intentos++;
                if(intentos==5){
                    System.out.println("Número de intentos excedido");
                    this.inicioSesion();
                }
            }
        }
    }
}
