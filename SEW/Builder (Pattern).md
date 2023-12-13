*author: Nico Zimmermann
date created: 13.12.2023*
- - -
## Allgemein

https://howtodoinjava.com/design-patterns/creational/builder-pattern-in-java/

Das Builder Entwurfsmuster ist eine Möglichkeit Objekte zu erstellen. Es hilft bei der Erstellung unveränderlicher Objekte, die eine große Anzahl von Eigenschaften aufweisen. 
Indem es eine klare API zur Verfügung stellt, ermöglicht der Builder die Erstellung von Objekten in einer gut lesbaren und wartbaren Weise. Dies geschieht durch das Anbieten von Methoden zum Hinzufügen von Eigenschaften oder Parametern, wodurch eine schrittweise Konfiguration des zu erstellenden Objekts ermöglicht wird.

Der Vorteil des Builder-Musters liegt in seiner Fähigkeit, unveränderliche (immutable) Objekte zu erzeugen. Dies bedeutet, dass einmal erstellte Objekte nach ihrer Erstellung nicht mehr geändert werden können, was unter anderem Vorteile in Bezug auf Thread-Sicherheit und Vermeidung unerwarteter Veränderungen bietet.

Ein typisches Beispiel in Java ist die Verwendung von Builder-Patterns in Verbindung mit Fluent Interfaces, um die Lesbarkeit des Codes zu verbessern und die Erstellung von Objekten mit einer großen Anzahl von Parametern zu vereinfachen.

_ _ _
## Beispiel
Wenn man von einem User Objekt ausgeht, das 5 **final** Eigenschaften besitzt (firstName, lastName, age, phone, address) wovon nur **firstName** und **lastName** verpflichtend sind, führt das zu einer hohen Anzahl von Konstruktoren.

Das Builder Pattern bietet eine elegante Lösung bei der die Unveränderlichkeit der Objekte vorhanden bleibt. 

![[uml-of-builedr.jpg|350]]

```java
public static void main (String[]args){
	User user1 = new User.UserBuilder("Bart", "Simpson")
		.age(13)
		.phone("187187187")
		.address("Springfield ?")
		.build();
	System.out.println(user1);
}
```

```java
public static void main (String[]args){
	User user2 = new User.UserBuilder("James", "Bond")
		.age(52)
		.phone("007")
		// no address
		.build();
	System.out.println(user2);
}
```

```java
public static void main (String[]args){
	User user3 = new User.UserBuilder("Super", "Man")
		// no age
		// no phone
		// no address
		.build();
	System.out.println(user3);
}
```

Die konkrete Implementierung des UserBuilder findet sich im Projekt BuilderPattern.