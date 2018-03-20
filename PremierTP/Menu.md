```Java
public class Testmenu {

    public static int menu() throws IOException {

        int selection;
        //Ceci efface en principe un écran (console) Linux et Windows
        System.out.print("\033[H\033[2J");
        System.out.flush();
        Scanner input = new Scanner(System.in);

        /**
         * ************************************************
         */
        System.out.println("0 - Quitter");
        System.out.println("-------------------------");
        System.out.println("1 - Créer");
        System.out.println("2 - Mise à jour");
        System.out.println("3 - Suprimer");
        System.out.println("4 - Consulter");
        System.out.print("Choisir : ");

        selection = input.nextInt();
        return selection;
    }

    /**
     * @param args 
     * @throws java.io.IOException
     */
    public static void main(String[] args) throws IOException {
        int choix = menu();
        System.out.printf("\nVous avez choisi %d\n",choix);
    }

}
```