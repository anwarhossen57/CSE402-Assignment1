# CSE402: Software Engineering Lab
## Assignment on Creational Design Patterns (Abstract Factory)

This project extends an existing Java implementation of the **Abstract Factory Design Pattern** by adding support for a new product family: **Plane**.

---

## 📊 System Architecture & UML Visualization

Below is the dynamically generated **UML Class Diagram** showing the updated system structure. It includes the new `Plane` family (`Boeing`, `Airbus`) and the new `Planefactory`, mapping directly to the requirements based on `UML_2.jpg`.

![Updated Abstract Factory UML Diagram](https://www.plantuml.com/plantuml/svg/bPBDRi8m48Rl_XNSRv1H2W92e8Y5Hfe4Y64IebXpS6KMc-X1bQ1m9_lzvU4C3tU-lz_ttM6pY8pD0bHaqFAn-K0r7g7Oun_7I835i7iAn4fL1G6bO9HAs0_mB2YFjWfU-r9Z4I03O26m1T5wG8I-1Blyw62gB1-m49iWw2vW67Sj6T8wM1-O49mYyZ5O6P_7ZlwK8Y_8X5wS7ApyC7AnC5AnS_OoySbyC3AmG3_yM5_A1e_8K5AnApyCS3v_3t_7RkwK6Y_8X_wS3ApyC5AmO5AmS_Oox_K_v7X_N6kX_7Vpy_W0)

---

## 🛠️ Modifications Implemented

As specified in `Assignment-1.pdf`, the following modifications and additions have been introduced:

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

## 📦 How to Run the Project

1. Open the project inside your preferred Java IDE (Eclipse/IntelliJ/NetBeans) or run via terminal.
2. Compile all `.java` source files.
3. Execute the `FactoryDemo` class to view the terminal logs showcasing sequential object allocation for Cars, Boats, and Planes.
