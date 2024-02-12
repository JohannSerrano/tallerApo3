# tallerApo3
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package umariana.taller1;
//Importamos La contenedora dinamica
import java.util.ArrayList;
//Importamos la interaccion del usuario hacia la consola para llenar datos
import java.util.Scanner;
//Importamos la clase mundo
import mundo.Tarea;


/**
 * @author Johan
 */
public class Taller1 {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    
    Scanner lector=new Scanner(System.in);
    //Variable para iniciar el menu
    boolean activo= true;
    //Variable que Evita opciones 2 y 3 sin opción inicial.
    boolean tareaAgregada=false;
    //Contenedora Dinamica para llenar los datos
    ArrayList<Tarea> misTareas=new ArrayList<>();
    //Comienzo del menu
    do{
            System.out.println("===Menu de Opciones===\n");
            //Aqui se pide al usuario que ingrese a alguna de las opciones
            System.out.println("==Seleccione una opcion==\n"+"1 Opcion Agregar Tarea\n"+"2 Opcion Mostrar Taareas\n"+"3 Listado de tareas\n"+"4 Salir Del Programa");
            int opcion = lector.nextInt();
            //Ingreso a diferentes opciones
            switch(opcion){
                case 1:
                    //Ingreso de datos
                    System.out.println("====AGREGAR TAREA====");

                    System.out.println("Ingrese el id de la tarea");
                    int idTarea = lector.nextInt();

                    lector.nextLine();
                    System.out.println("Ingrese la descripcion de la tarea");
                    String descripcion = lector.nextLine();

                    int prioridad;
                    //Cumplimiento de los parametros de la prioridad
                    do {
                        System.out.println("Ingrese la prioridad de la tarea del 1-5");
                        prioridad = lector.nextInt();
                        if (prioridad < 1 || prioridad > 5) {
                            System.out.println("La prioridad debe estar entre 1 a 5. Inténtelo de otra vez.");
                        }else{
                            
                        }
                    } while (prioridad < 1 || prioridad > 5);

                    // Creacion del objeto y llenar la informacion
                    Tarea nuevaTarea = new Tarea(idTarea, descripcion, prioridad);
                    // Almacenar el objeto en la contenedora
                    misTareas.add(nuevaTarea);
                    tareaAgregada=true;
                    System.out.println("Tarea Agregada Satisfactoriamente");
                    break;
                case 2:
                    //Condición previa para mostrar datos.
                    if(tareaAgregada==false){
                        System.out.println("No hay tareas Agregadas\nPor favor Agrega una tarea Antes");
                    }else{
                //Mostrar tareas por orden de agregado
                System.out.println("====TAREAS REGISTRADAS====");
                for(Tarea t: misTareas){
                    System.out.println("Id: "+t.getIdTarea());
                    System.out.println("Descripcion: "+t.getDescripcion());
                    System.out.println("Prioridad: "+t.getPrioridad());
                    System.out.println("==================");
                }  
                }
                break;
                case 3:

                    //Condición previa para mostrar datos.
                    if (tareaAgregada == false) {
                        System.out.println("No hay tareas Agregadas\nPor favor Agrega una tarea Antes");
                    }else{
                        System.out.println("====TAREAS POR PRIORIDAD====");
                        // Ordenar las tareas por prioridad
                        for (int i = 5; i >= 1; i--){
                            for (Tarea t : misTareas){
                                if (t.getPrioridad() == i){
                                    System.out.println("Id: " + t.getIdTarea());
                                    System.out.println("Descripción: " + t.getDescripcion());
                                    System.out.println("Prioridad: " + t.getPrioridad());
                                }
                            }
                        }
                    }

                break;
                //Salida del menu y programa
                case 4:
                    System.out.println("Saliste del programa");
                    activo=false;
                    break;
                //Imprime este mensaje si el usuario escoje una opcion que no este disponible
                default:
                System.out.println("Opcion no valida");
            }
    }while(activo);
    
}
}
