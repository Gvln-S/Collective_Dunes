# [CollectiveDunes ](https://github.com/Gvln-S/Collective_Dunes)

**CollectiveDunes** is an interactive, real-time multiplayer web application that brings the classic "falling sand" simulation to a collaborative environment. Built with a robust **Spring Boot** backend and a high-performance **TypeScript** frontend, the application leverages a **Service-Oriented Architecture (SOA)** to ensure seamless synchronization and real-time interaction among multiple users.

![Java](https://img.shields.io/badge/Java-23-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3.5-6DB33F?style=for-the-badge&logo=spring&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-Frontend-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket-Real_Time-010101?style=for-the-badge)


## The Challenge: Multiplayer Falling Sand

The "falling sand" genre is a classic programming challenge that requires efficient cellular automata algorithms to calculate physics (gravity, collision, state changes of materials like sand, water, or stone) frame by frame. 

**CollectiveDunes** takes this challenge to the next level by making it **multiplayer**. It synchronizes the canvas state across multiple connected clients in real-time, ensuring that when one user drops sand, everyone sees the impact instantly.

## Architecture & Patterns

The project is structured around a **Service-Oriented Architecture (SOA)** and utilizes several modern design patterns to handle the high throughput required by a real-time physics simulation:

* **Event-Driven Synchronization:** Uses **WebSockets** and Spring WebFlux to broadcast grid updates (state changes) to all connected clients with minimal latency.
* **Decoupled Frontend/Backend:** The physics rendering and grid calculations are optimized on the client side via TypeScript (`SandboxFunctions.ts`), while the backend acts as the authoritative source of truth and event router.
* **In-Memory Data Grid:** Utilizes an **H2 Database** for rapid, lightweight session management and state persistence without the overhead of external disk I/O during active simulations.

## Key Features

* **Real-Time Collaboration:** Multiple users can interact with the same physics canvas simultaneously.
* **TypeScript Physics Engine:** Highly optimized cellular automata logic implemented in `SandboxFunctions.ts` for smooth browser rendering.
* **Spring Boot Backend:** Reliable routing, session handling, and WebSocket communication.
* **Zero-Config Database:** Uses H2 in-memory database for immediate out-of-the-box execution.

## Installation & Setup

### Prerequisites
* **Java 23** (JDK 23)
* **Maven** (3.6+ or use the included `mvnw` wrapper)
* **Node.js / npm** (For compiling TypeScript files)

### Running the Application

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/Gvln-S/CollectiveDunes.git](https://github.com/Gvln-S/CollectiveDunes.git)
    cd CollectiveDunes
    ```

2.  **Build the project:**
    Compile the Java backend. The `-DskipTests` flag is recommended for the first build.
    ```bash
    mvn clean package -DskipTests
    ```

3.  **Start the Server:**
    ```bash
    mvn spring-boot:run
    ```

4.  **Access the Application:**
    * **Main Simulator:** Open your browser and navigate to `http://localhost:8080` (or `8081` if the port was changed).
    * **H2 Database Console:** Navigate to `http://localhost:8080/h2-console`. 
        * *JDBC URL:* `jdbc:h2:mem:dunesdb`
        * *User:* `sa`
        * *Password:* *(leave blank)*

## Contributing and Forking

Whether you want to add new elements (like fire, acid, or oil), improve the cellular automata algorithm, or scale the backend to support massive MMO-style canvases, contributions are welcome! 

Feel free to **fork** this repository, apply your own architectural tweaks, and submit a Pull Request. Let's build the ultimate collaborative sandbox together!

| img 1 | 
| :---: |
| ![Screenshot 1](img/github_one.png) | 
---
*Developed with a passion for cellular automata and real-time systems.*
