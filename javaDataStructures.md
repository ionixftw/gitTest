# Java Data Structures

## What is a package?

* Packages are a nice way to bundle related java files

## Package Naming Conventions

* Package name folows the reverse domain naming scheme
* Ex: cf.stonecold.className

## Creating and using a  package

* To create a package simply put your java file inside the the reverse domain directory
* Ex: If the class name is Football that needs to be stored in  cf.stonecold package put the Football.java file in cf/stonecold/ directory
* On top of the Football.java file add the package name
* Ex: 

```java
/* workingDirectory/cf/stonecold/Football.java*/
package cf.stonecold;

public class Football {
}
```
* To use Football class in other classes you need to import it first
* Ex: 

```java
/* workingDirectory/Example.java */
import cf.stonecold.Football;

public class Example {
    public static void main(String[] args) {
        Football football = new Football();
    }
}
```

