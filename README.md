@startuml
skinparam classAttributeIconSize 0
skinparam monochrome false
skinparam packageStyle rectangle

' --- INTERFACES & PRODUCTS ---

interface Car {
    + getmileage() : void
    + drive() : void
}

class Sedan implements Car {
    + getmileage() : void
    + drive() : void
}

class SUV implements Car {
    + getmileage() : void
    + drive() : void
}

interface Boat {
    + getweight() : void
    + row() : void
}

class SpeedBoat implements Boat {
    + getweight() : void
    + row() : void
}

class FishingBoat implements Boat {
    + getweight() : void
    + row() : void
}

' --- NEWLY ADDED PLANE FAMILY ---
interface Plane {
    + fly() : void
    + getCapacity() : int
}

class Boeing implements Plane {
    + fly() : void
    + getCapacity() : int
}

class Airbus implements Plane {
    + fly() : void
    + getCapacity() : int
}

' --- FACTORIES ---

interface AbstractFactory {
    + getCar(car : String) : Car
    + getBoat(boat : String) : Boat
    + getPlane(plane : String) : Plane
}

class Carfactory implements AbstractFactory {
    + getCar(car : String) : Car
    + getBoat(boat : String) : Boat
    + getPlane(plane : String) : Plane
}

class Boatfactory implements AbstractFactory {
    + getBoat(boat : String) : Boat
    + getCar(car : String) : Car
    + getPlane(plane : String) : Plane
}

' --- NEWLY ADDED PLANE FACTORY ---
class Planefactory implements AbstractFactory {
    + getPlane(plane : String) : Plane
    + getCar(car : String) : Car
    + getBoat(boat : String) : Boat
}

' --- CLIENT & DEMO ---

class Producer {
    + getFactory(factory : String) : AbstractFactory
}

class FactoryDemo {
    + main(args : String[]) : void
}

' --- RELATIONSHIPS & CREATES ---

Carfactory --> Sedan : creates
Carfactory --> SUV : creates

Boatfactory --> SpeedBoat : creates
Boatfactory --> FishingBoat : creates

' New Connections
Planefactory --> Boeing : creates
Planefactory --> Airbus : creates

Producer .> AbstractFactory : uses
FactoryDemo .> Producer : uses

@endum
