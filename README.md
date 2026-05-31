# CSE402: Software Engineering Lab
## Assignment on Creational Design Patterns (Abstract Factory)

This project extends an existing Java implementation of the **Abstract Factory Design Pattern** by adding support for a new product family: **Plane**.

---

## 🛠️ System Architecture & UML Updates

As specified in `Assignment-1.pdf` and based on the baseline `UML.jpg`, the following modifications and additions have been introduced to fullfill the pattern's structural requirements:

### 1. New Product Family (Plane)
- **`Plane` (Interface):** Declares core behaviors for all aircraft components (`fly()` and `getCapacity()`).
- **`Boeing` (Concrete Class):** Implements `Plane`, providing specific execution logic for Boeing aircraft.
- **`Airbus` (Concrete Class):** Implements `Plane`, providing specific execution logic for Airbus aircraft.

### 2. Factory Layer Modifications
- **`AbstractFactory` (Updated):** Added the abstract factory method `public abstract Plane getPlane(String plane);` to enforce conformity across all sub-factories.
- **`Carfactory` & `Boatfactory` (Updated):** Overrode the new `getPlane()` method to return `null`, keeping their core product boundaries secure.
- **`Planefactory` (New Class):** Extends/Implements `AbstractFactory` to handle instance creation requests specifically for `"BOEING"` and `"AIRBUS"`.

### 3. Client & Demo Modifications
- **`Producer` (Updated):** Enhanced the control flow within `getFactory(String choice)` to return an instance of `Planefactory` whenever `"PLANE"` is requested.
- **`FactoryDemo` (Updated):** Included testing routines that request `Planefactory`, instantiate both `Boeing` and `Airbus` objects, and execute their corresponding methods to verify runtime behavior.

---

## 📊 UML Diagram Relationship Mapping

When rendering the updated `UML.jpg`, the structural arrows are mapped as follows:
1. **Realization (`---▷`):** 
   - `Boeing` and `Airbus` point upwards to the `Plane` interface box.
   - `Planefactory` points towards the central `AbstractFactory` interface box.
2. **Dependency / Creation (`--->`):** 
   - `Planefactory` connects to both `Boeing` and `Airbus` with a relationship indicator labeled **"creates"**.

---

## 📦 How to Run the Project

1. Open the project inside your preferred Java IDE (Eclipse/IntelliJ/NetBeans) or run via terminal.
2. Compile all `.java` source files.
3. Execute the `FactoryDemo` class to view the terminal logs showcasing sequential object allocation for Cars, Boats, and Planes.
