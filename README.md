# Protected-Modifier-and-Exception-Handling

## Explain the protected access modifier in Java. In which scenarios is it most useful, and how does it differ from private and public modifiers?
The protected access modifier in Java allows a member (fields or methods) of a class to be accessible in the same package and also in subclasses, even if they are in different packages. It strikes a balance between package-private (default) access and public access, allowing controlled visibility.  

Differences from Other Modifiers  
Private: Accessible only within the same class. It provides the most restricted access.  
Public: Accessible from anywhere in the application, offering the least restricted access.  
Protected: Accessible within the same package and by subclasses, even if they are outside the package.    
## If a class is defined in one package and a subclass is defined in another package, can the subclass access the protected members of the superclass? Provide an example to illustrate your answer.
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
Superclass Definition: In the com.example.package1 package, the SuperClass has a protected field message and a protected method displayMessage().  
Subclass Definition: In the com.example.package2 package, the SubClass extends SuperClass. It can access the protected field and method because it is a subclass.  
Accessing Protected Members: In the SubClass, the show() method accesses the message field and displayMessage() method directly, illustrating that protected members are accessible through inheritance, even across different packages.  
Main Class: The Main class creates an instance of SubClass and calls the show() method, which demonstrates the access to the protected members.  
This example shows how the protected access modifier allows subclass access across package boundaries through inheritance.

