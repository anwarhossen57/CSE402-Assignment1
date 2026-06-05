```mermaid
classDiagram
    class AbstractFactory {
        <<interface>>
        +getCar(car : String) : Car
        +getBoat(boat : String) : Boat
        +getPlane(plane : String) : Plane
    }

    class Car {
        <<interface>>
        +getmileage() : void
        +drive() : void
    }

    class Boat {
        <<interface>>
        +getweight() : void
        +row() : void
    }

    class Plane {
        <<interface>>
        +fly() : void
        +getCapacity() : void
    }

    class Sedan {
        +getmileage() : void
        +drive() : void
    }

    class SUV {
        +getmileage() : void
        +drive() : void
    }

    class SpeedBoat {
        +getweight() : void
        +row() : void
    }

    class FishingBoat {
        +getweight() : void
        +row() : void
    }

    class Boeing {
        +fly() : void
        +getCapacity() : void
    }

    class Airbus {
        +fly() : void
        +getCapacity() : void
    }

    class Carfactory {
        +getCar(car : String) : Car
        +getBoat(boat : String) : Boat
        +getPlane(plane : String) : Plane
    }

    class Boatfactory {
        +getBoat(boat : String) : Boat
        +getCar(car : String) : Car
        +getPlane(plane : String) : Plane
    }

    class Planefactory {
        +getPlane(plane : String) : Plane
        +getCar(car : String) : Car
        +getBoat(boat : String) : Boat
    }

    class Producer {
        +getFactory(factory : String) : AbstractFactory
    }

    class FactoryDemo {
        +main(args : String[]) : void
    }

    %% Relationships
    Sedan ..|> Car
    SUV ..|> Car
    SpeedBoat ..|> Boat
    FishingBoat ..|> Boat
    Boeing ..|> Plane
    Airbus ..|> Plane

    Carfactory ..|> AbstractFactory
    Boatfactory ..|> AbstractFactory
    Planefactory ..|> AbstractFactory

    Carfactory --> Sedan : creates
    Carfactory --> SUV : creates
    Boatfactory --> SpeedBoat : creates
    Boatfactory --> FishingBoat : creates
    Planefactory --> Boeing : creates
    Planefactory --> Airbus : creates

    Producer ..> AbstractFactory : uses
    FactoryDemo ..> Producer : uses
