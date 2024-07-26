# Protected-Modifier-and-Exception-Handling

## Explain the protected access modifier in Java. In which scenarios is it most useful, and how does it differ from private and public modifiers?
The protected access modifier in Java allows a member (fields or methods) of a class to be accessible in the same package and also in subclasses, even if they are in different packages. It strikes a balance between package-private (default) access and public access, allowing controlled visibility.  

Differences from Other Modifiers  
Private: Accessible only within the same class. It provides the most restricted access.  
Public: Accessible from anywhere in the application, offering the least restricted access.  
Protected: Accessible within the same package and by subclasses, even if they are outside the package.    

Accessing Protected Members Across Packages  
Suppose you have a superclass defined in one package and a subclass in another package. The subclass can access the protected members of the superclass through inheritance, but not directly using an instance of the superclass.
```
// File: com.example.package1.SuperClass.java
package com.example.package1;

public class SuperClass {
    protected void display() {
        System.out.println("Protected method in SuperClass");
    }
}

// File: com.example.package2.SubClass.java
package com.example.package2;

import com.example.package1.SuperClass;

public class SubClass extends SuperClass {
    public void show() {
        display(); // Accessing protected method of SuperClass
    }
}

// File: com.example.package2.Main.java
package com.example.package2;

public class Main {
    public static void main(String[] args) {
        SubClass obj = new SubClass();
        obj.show(); // Outputs: Protected method in SuperClass
    }
}
```
