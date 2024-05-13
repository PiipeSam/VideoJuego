# VideoJuego
App para facilitar la gestión de los videojuegos
import java.util.ArrayList;
import java.util.Scanner;

class Videojuego {
    private String titulo;
    private String genero;
    private int anioLanzamiento;

    public Videojuego(String titulo, String genero, int anioLanzamiento) {
        this.titulo = titulo;
        this.genero = genero;
        this.anioLanzamiento = anioLanzamiento;
    }

    public String getTitulo() {
        return titulo;
    }

    public String getGenero() {
        return genero;
    }

    public int getAnioLanzamiento() {
        return anioLanzamiento;
    }

    @Override
    public String toString() {
        return "Videojuego{" +
                "titulo='" + titulo + '\'' +
                ", genero='" + genero + '\'' +
                ", anioLanzamiento=" + anioLanzamiento +
                '}';
    }
}

class GestorVideojuegos {
    private ArrayList<Videojuego> listaVideojuegos;

    public GestorVideojuegos() {
        this.listaVideojuegos = new ArrayList<>();
    }

    public void agregarVideojuego(Videojuego videojuego) {
        listaVideojuegos.add(videojuego);
    }

    public void mostrarVideojuegos() {
        for (Videojuego videojuego : listaVideojuegos) {
            System.out.println(videojuego);
        }
    }

    public void eliminarVideojuego(String titulo) {
        listaVideojuegos.removeIf(videojuego -> videojuego.getTitulo().equals(titulo));
    }

    public void buscarPorTitulo(String titulo) {
        for (Videojuego videojuego : listaVideojuegos) {
            if (videojuego.getTitulo().equalsIgnoreCase(titulo)) {
                System.out.println(videojuego);
                return;
            }
        }
        System.out.println("No se encontró ningún videojuego con ese título.");
    }

    public void buscarPorGenero(String genero) {
        for (Videojuego videojuego : listaVideojuegos) {
            if (videojuego.getGenero().equalsIgnoreCase(genero)) {
                System.out.println(videojuego);
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        GestorVideojuegos gestor = new GestorVideojuegos();

        // Ejemplo de cómo agregar videojuegos
        gestor.agregarVideojuego(new Videojuego("The Legend of Zelda: Breath of the Wild", "Aventura", 2017));
        gestor.agregarVideojuego(new Videojuego("Red Dead Redemption 2", "Acción", 2018));
        gestor.agregarVideojuego(new Videojuego("Cyberpunk 2077", "RPG", 2020));

        // Mostrar la lista de videojuegos
        System.out.println("Lista de videojuegos:");
        gestor.mostrarVideojuegos();

        // Eliminar un videojuego
        System.out.println("\nIngrese el título del videojuego que desea eliminar:");
        String tituloEliminar = scanner.nextLine();
        gestor.eliminarVideojuego(tituloEliminar);

        // Mostrar la lista actualizada de videojuegos
        System.out.println("\nLista de videojuegos después de eliminar:");
        gestor.mostrarVideojuegos();

        // Buscar por título
        System.out.println("\nIngrese el título del videojuego que desea buscar:");
        String tituloBuscar = scanner.nextLine();
        System.out.println("\nResultado de la búsqueda por título:");
        gestor.buscarPorTitulo(tituloBuscar);

        // Buscar por género
        System.out.println("\nIngrese el género del videojuego que desea buscar:");
        String generoBuscar = scanner.nextLine();
        System.out.println("\nResultado de la búsqueda por género:");
        gestor.buscarPorGenero(generoBuscar);
    }
}



