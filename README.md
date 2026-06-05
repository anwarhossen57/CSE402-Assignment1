```mermaid
classDiagram
    %% 1. INTERFACES & CLASSES DECLARATION WITH PROPERTIES
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

    %% 2. INHERITANCE AND IMPLEMENTS (vertical alignment)
    Sedan ..|> Car
    SUV ..|> Car
    SpeedBoat ..|> Boat
    FishingBoat ..|> Boat
    Boeing ..|> Plane
    Airbus ..|> Plane

    Carfactory ..|> AbstractFactory
    Boatfactory ..|> AbstractFactory
    Planefactory ..|> AbstractFactory

    %% 3. CREATION RELATIONSHIPS
    Carfactory --> Sedan : creates
    Carfactory --> SUV : creates
    Boatfactory --> SpeedBoat : creates
    Boatfactory --> FishingBoat : creates
    Planefactory --> Boeing : creates
    Planefactory --> Airbus : creates

    Producer ..> AbstractFactory : uses
    FactoryDemo ..> Producer : uses

    %% 4. LAYOUT POSITIONING TRICKS (forcing 3 neat columns like your image)
    Carfactory ---- Boatfactory : invisible
    Carfactory ---- Planefactory : invisible
    Car ---- AbstractFactory : invisible
    AbstractFactory ---- Boat : invisible
    Boat ---- Plane : invisible

    %% 5. COLOR THEMES MATCHING YOUR ORIGINAL IMAGE
    %% Purple Titles (Interfaces)
    style AbstractFactory fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000
    style Car fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000
    style Boat fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000
    style Plane fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000

    %% Blue Classes (Concrete Products)
    style Sedan fill:#D6EAF8,stroke:#2E86C1,stroke-width:1px,color:#000
    style SUV fill:#D6EAF8,stroke:#2E86C1,stroke-width:1px,color:#000
    style SpeedBoat fill:#D6EAF8,stroke:#2E86C1,stroke-width:1px,color:#000
    style FishingBoat fill:#D6EAF8,stroke:#2E86C1,stroke-width:1px,color:#000
    style Boeing fill:#D6EAF8,stroke:#2E86C1,stroke-width:1px,color:#000
    style Airbus fill:#D6EAF8,stroke:#2E86C1,stroke-width:1px,color:#000

    %% Green Factories
    style Carfactory fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#000
    style Boatfactory fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#000
    style Planefactory fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#000

    %% Yellow & Red Core Engine (Center Bottom)
    style Producer fill:#FCF3CF,stroke:#F39C12,stroke-width:2px,color:#000
    style FactoryDemo fill:#FADBD8,stroke:#CB4335,stroke-width:2px,color:#000
