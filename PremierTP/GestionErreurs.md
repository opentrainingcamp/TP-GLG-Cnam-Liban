# COMPLEMENT : Gestion des erreurs


Tout programme comporte des erreurs. C'est à cause de cette constatation que les développeurs essaient d'en réduire le nombre au maximum. Mais malgré cela, toutes les erreurs ne peuvent être prévisibles.

Les erreurs syntaxiques sont interceptées lors de la compilation, mais il reste encore souvent des erreurs « imprévisibles ». Elles se produisent généralement de façon exceptionnelle, c'est-à-dire à la suite d'une action de l'utilisateur, ou de l'environnement. Une première solution pour palier ce problème consiste à mettre en place un système de code d'erreur. Cette technique rend difficile la lecture et l'écriture des programmes (imbrication de test conditionnel if...else...).

Java propose un mécanisme de gestion d'exceptions, consistant à effectuer les instructions dans un bloc d'essai (le bloc try) qui surveille les instructions. Lors de l'apparition d'une erreur, celle-ci est lancée dans un bloc de traitement d'erreur (le bloc catch) sous forme d'un objet appelé Exception. Ce block catch peut alors traiter l'erreur ou la relancer vers un bloc de plus haut niveau. Un dernier block, finally, permet toujours d'exécuter une suite d'instructions qu'il y ait eu ou non exception. Il sert, par exemple, à ce qu'un fichier ouvert dans le bloc try soit systématiquement refermé, quoiqu'il arrive, grâce au bloc finally.

Lorsque le programme rencontre une erreur dans un bloc try, une exception est instanciée puis lancée. L'interpréteur cherche un bloc catch à partir de l'endroit où l'exception a été créée. S'il ne trouve aucun bloc catch, l'exception est lancée dans le bloc de niveau supérieur et ainsi de suite jusqu'au bloc de la classe qui, par défaut, enverra l'exception à l'interpréteur. Celui-ci émettra alors un message d'alerte standard pour le type d'exception. Si un bloc catch est trouvé, celui-ci gérera l'exception et ne l'enverra pas à l'interpréteur.

Si par contre on désire que l'exception soit traitée par les blocs de niveaux supérieurs, il suffit d'inclure à la fin de la série d'instructions contenues dans le bloc catch une clause throw, suivie du type de l'exception entre parenthèse, puis du nom de l'exception. Ainsi l'exception continuera son chemin...

Le mécanisme décrit ci-dessus, correspond aux exceptions contrôlées. Celles-ci doivent hériter de la classe java.lang.Exception. Par contre, les exceptions non contrôlées, comme leur non l'indique n'oblige pas le compilateur à exiger des blocks try/catch. Les exceptions non contrôlées (héritant de RuntimeException) peuvent ne pas être interceptées ou traitées.

Hello PetStore !
Cet exemple vous montre les différences de code entre une exception contrôlée et non contrôlée!

```Java 
public class HelloPetstore {
  // Point d'entrée de l'application
  public static void main(String args) {
    // si vous passez l'argument "controlee"
    if (args[0].equals("controlee")) { (1)
      try {
        controlee(); (2)
        System.out.println("Ce texte ne s'affichera pas");
      } catch (Exception e) {
        System.out.println("Hello"); (5)
      } finally {
        System.out.println("PetStore!");
      }
    } else {
      noncontrolee(); (6)
      System.out.println("Ce texte ne s'affichera pas");
    }
  }
  private static void controlee() throws Exception { (4)
    throw new Exception(); (3)
  }
  private static void noncontrolee() {
    throw new RuntimeException(); (7)
  }
}
```

Exécutez ce programme en lui passant le paramètre « controlee » (java HelloPetstore controlee)(1) la méthode privée controlee() est appelée (2). Cette méthode lance une exception contrôlée (3) et, est donc obligée de la déclarer dans sa signature (4). La classe Exception est la classe mère de toutes les exceptions contrôlées. L'appel de cette méthode doit donc être entouré d'un block try/catch (5).

À l'opposé, si vous passez un autre paramètre au programme, la méthode noncontrolee() est appelée (6). Elle lance une RuntimeException (classe mère des exceptions non contrôlées) et n'a pas besoin de la déclarer dans sa signature (7). L'appel n'a donc pas besoin d'être entouré d'un block try/catch.

Après compilation de cette classe, voici la trace de l'exécution du programme avec les différents paramètres :

java HelloPetstore controlee
Hello
PetStore!
java HelloPetstore noncontrolee
Exception in thread "main" java.lang.RuntimeException
  at HelloPetstore.noncontrolee(HelloPetstore.java:34)
  at HelloPetstore.main(HelloPetstore.java:23)


La pile d'exécution est affichée (8) par l'interpréteur. Cela permet de suivre l'origine de l'exception. Dans notre cas l'exception de type Runtime est levée à la ligne 34 de la classe HelloPetstore.