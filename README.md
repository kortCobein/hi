toString(): “Es un método que devuelve la información de un objeto en forma de texto. Normalmente se sobrescribe con @Override para decidir cómo quiero que se muestre el objeto cuando lo imprimo.”

Clase abstracta: “Es una clase que sirve como base para otras clases, pero no se puede instanciar directamente con new. Puede tener atributos, constructor, getters, setters, métodos normales y métodos abstractos.”

Método abstracto: “Es un método que se declara pero no tiene cuerpo. Obliga a las clases hijas a implementarlo y decidir cómo se va a ejecutar.”

Interfaz: “Es como un contrato. Declara métodos que una clase se compromete a implementar usando implements. Sirve para obligar a distintas clases a tener ciertos comportamientos aunque no pertenezcan necesariamente a la misma herencia.”

Diferencia rápida entre clase abstracta e interfaz:

“Una clase abstracta se usa principalmente para compartir una base común, atributos y comportamiento entre clases relacionadas. Una interfaz se usa para definir capacidades o comportamientos que una clase debe cumplir.”

Ejemplo oral corto:

abstract class Empleado {
    public abstract void trabajar();
}

“Empleado es abstracta y trabajar() es abstracto porque todavía no se define cómo trabaja cada tipo de empleado.”

class Docente extends Empleado {

    @Override
    public void trabajar() {
        System.out.println("Dando clase");
    }
}

“Docente hereda de Empleado y está obligado a implementar trabajar().”

Interfaz:

interface Evaluable {
    void evaluar();
}

class Docente extends Empleado implements Evaluable {

    @Override
    public void trabajar() {
        System.out.println("Dando clase");
    }

    @Override
    public void evaluar() {
        System.out.println("Evaluando");
    }
}

Para memorizarlo rápido:

abstract class = base que no puedo instanciar.
abstract method = método sin cuerpo que el hijo debe completar.
interface = contrato de métodos que debo cumplir.
toString() = cómo quiero representar mi objeto como texto. 
Va rápido:

class Empleado {
    String nombre;

    public void trabajar() {
        System.out.println("Empleado trabajando");
    }
}

class Docente extends Empleado {

    @Override
    public void trabajar() {
        System.out.println("Docente dando clase");
    }
}

class Administrativo extends Empleado {

    @Override
    public void trabajar() {
        System.out.println("Administrativo trabajando en oficina");
    }
}

Aquí tienes un padre:

Empleado

y dos hijos:

Docente
Administrativo

La herencia está aquí:

class Docente extends Empleado
class Administrativo extends Empleado

Ahora, esto NO es realmente donde estás aprovechando el polimorfismo:

Docente d = new Docente();
Administrativo a = new Administrativo();

d.trabajar();
a.trabajar();

Funciona, pero cada variable ya está declarada directamente como su propia clase.

El polimorfismo se ve más claro aquí:

Empleado e1 = new Docente();
Empleado e2 = new Administrativo();

e1.trabajar();
e2.trabajar();

Ambas variables son declaradas como:

Empleado

pero contienen objetos distintos:

new Docente()
new Administrativo()

Y la salida sería:

Docente dando clase
Administrativo trabajando en oficina

Ese es el punto del polimorfismo: usar un mismo tipo padre para manejar distintos hijos, y que cada hijo responda con su propio comportamiento.

En corto para el oral:

> Herencia es cuando una clase hija adquiere características del padre con extends. Polimorfismo es cuando puedo usar una referencia del padre para guardar distintos objetos hijos y ejecutar el comportamiento específico de cada uno.



La diferencia clave es:

Docente d = new Docente();       // herencia existe, pero no aprovecho polimorfismo

Empleado e = new Docente();      // herencia + polimorfismo

Y ojo: para que Empleado e = new Docente(); funcione, primero tiene que existir la relación de herencia Docente extends Empleado.