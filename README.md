```mermaid
flowchart TB
    %% 1. CAR FAMILY GRAPH
    subgraph Car_Family [Car Product Family]
        direction TB
        Car_Int["«interface»<br/><b>Car</b><br/>---<br/>+getmileage() : void<br/>+drive() : void"]
        Sedan["<b>Sedan</b><br/>---<br/>+getmileage() : void<br/>+drive() : void"]
        SUV["<b>SUV</b><br/>---<br/>+getmileage() : void<br/>+drive() : void"]
        Carfactory["<b>Carfactory</b><br/>---<br/>+getCar(car : String) : Car<br/>+getBoat(boat : String) : Boat<br/>+getPlane(plane : String) : Plane"]
        
        Sedan --|> Car_Int
        SUV --|> Car_Int
        Carfactory -->|creates| Sedan
        Carfactory -->|creates| SUV
    end

    %% 2. CORE FACTORY ENGINE
    subgraph Core_Engine [Abstract Factory Engine]
        direction TB
        AbstractFactory["«interface»<br/><b>AbstractFactory</b><br/>---<br/>+getCar(car : String) : Car<br/>+getBoat(boat : String) : Boat<br/>+getPlane(plane : String) : Plane"]
        Producer["<b>Producer</b><br/>---<br/>+getFactory(factory : String) : AbstractFactory"]
        FactoryDemo["<b>FactoryDemo</b><br/>---<br/>+main(args : String[]) : void"]
        
        Producer --|> AbstractFactory
        FactoryDemo -.->|uses| Producer
    end

    %% 3. BOAT FAMILY GRAPH
    subgraph Boat_Family [Boat Product Family]
        direction TB
        Boat_Int["«interface»<br/><b>Boat</b><br/>---<br/>+getweight() : void<br/>+row() : void"]
        SpeedBoat["<b>SpeedBoat</b><br/>---<br/>+getweight() : void<br/>+row() : void"]
        FishingBoat["<b>FishingBoat</b><br/>---<br/>+getweight() : void<br/>+row() : void"]
        Boatfactory["<b>Boatfactory</b><br/>---<br/>+getBoat(boat : String) : Boat<br/>+getCar(car : String) : Car<br/>+getPlane(plane : String) : Plane"]
        
        SpeedBoat --|> Boat_Int
        FishingBoat --|> Boat_Int
        Boatfactory -->|creates| SpeedBoat
        Boatfactory -->|creates| FishingBoat
    end

    %% 4. PLANE FAMILY GRAPH
    subgraph Plane_Family [Plane Product Family]
        direction TB
        Plane_Int["«interface»<br/><b>Plane</b><br/>---<br/>+fly() : void<br/>+getCapacity() : void"]
        Boeing["<b>Boeing</b><br/>---<br/>+fly() : void<br/>+getCapacity() : void"]
        Airbus["<b>Airbus</b><br/>---<br/>+fly() : void<br/>+getCapacity() : void"]
        Planefactory["<b>Planefactory</b><br/>---<br/>+getPlane(plane : String) : Plane<br/>+getCar(car : String) : Car<br/>+getBoat(boat : String) : Boat"]
        
        Boeing --|> Plane_Int
        Airbus --|> Plane_Int
        Planefactory -->|creates| Boeing
        Planefactory -->|creates| Airbus
    end

    %% INTER-SUBGRAPH CONNECTIONS (CONNECTING TO ABSTRACT FACTORY)
    Carfactory -.->|implements| AbstractFactory
    Boatfactory -.->|implements| AbstractFactory
    Planefactory -.->|implements| AbstractFactory

    %% COLOR STYLES MATCHING THE ORIGINALS
    %% Purple Titles (Interfaces)
    style AbstractFactory fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000
    style Car_Int fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000
    style Boat_Int fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000
    style Plane_Int fill:#E8DAEF,stroke:#7D3C98,stroke-width:2px,color:#000

    %% Blue Classes (Products)
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

    %% Yellow & Red (Engine)
    style Producer fill:#FCF3CF,stroke:#F39C12,stroke-width:2px,color:#000
    style FactoryDemo fill:#FADBD8,stroke:#CB4335,stroke-width:2px,color:#000

    %% Subgraph Box Styling
    style Car_Family fill:#FAFAFA,stroke:#DDD,stroke-dasharray: 5 5
    style Boat_Family fill:#FAFAFA,stroke:#DDD,stroke-dasharray: 5 5
    style Plane_Family fill:#FAFAFA,stroke:#DDD,stroke-dasharray: 5 5
    style Core_Engine fill:#FDFEFE,stroke:#AEB6BF,stroke-width:2px
