Alien Invasion: Battle Simulation
=================================

1\. Project Overview
--------------------

This project is a C++ Object-Oriented simulation engine designed to model a battlefield conflict between an **Earth Army** and an **Alien Army**. The simulation operates in discrete time steps, generating units based on probabilistic inputs and managing them using custom-built Abstract Data Types (ADTs).

The primary goal of the application is to simulate unit generation, storage in specific data structures based on unit type, and eventually combat logic (Phase 1 currently covers generation and storage).

2\. Army Architecture & Unit Types
----------------------------------

The simulation distinguishes between two armies, each containing three specific unit types. Each unit type is managed by a distinct Data Structure chosen to represent its behavior on the battlefield.

All units inherit from the abstract base class Unit.

### 🌍 Earth Army

**Unit TypeClassDescriptionData StructureLogic & SourceEarth Soldier**ESStandard Infantry**LinkedQueue**

Deployed in FIFO (First-In, First-Out) order11.

**Earth Tank**ETHeavy Armor**ArrayStack**

Maintained in LIFO (Last-In, First-Out) order; newest tanks deploy first22.

**Earth Gunner**EGHigh Damage**priQueue**

**Priority Queue**. Priority is calculated as $\\sqrt{Health \\times Power}$, ensuring stronger units act first33.

### 👽 Alien Army

**Unit TypeClassDescriptionData StructureLogic & SourceAlien Soldier**ASStandard Infantry**LinkedQueue**

FIFO deployment4.

**Alien Monster**AMHeavy Unit**ArrayPointers**

Managed via a dynamic array of pointers for direct/random access5.

**Alien Drone**ADAerial/Fast**DoubleQueue**

A double-ended queue allowing simultaneous attacks from the front and rear6.

3\. Custom Data Structures (ADTs)
---------------------------------

The project implements template-based Data Structures from scratch to manage the units.

*   **LinkedQueue**: A standard Queue implementation using a linked list (FIFO)77.
    
*   **ArrayStack**: A Stack implementation using a static array (LIFO)8.
    

*   **priQueue**: A Priority Queue implemented as a sorted linked list.
    
    *   _Implementation:_ Uses priNode which stores a priority integer. The enqueue method uses insertion sort logic to place high-priority nodes at the head.
        
*   **ArrayPointers**: A custom container managing a dynamic array of pointers, specifically designed for AM units10101010.
    

4\. Simulation Flow & Input
---------------------------

### Random Generation (RandGen)

The RandGen class handles the creation of units based on configuration:

1.  **Probability Check:** A global probability (prob) determines if _any_ unit is generated at a specific timestep.
    
2.  **Type Selection:** If generation occurs, random percentages determine if the unit is a Soldier, Tank/Monster, or Gunner/Drone.
    
3.  **Stat Randomization:** Health, Power, and Attack Capacity are randomized within min/max ranges provided in the input file.
    

### Input File Format

The Game::ReadInput function parses a text file to configure the simulation. The expected format is11:

Plaintext

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   N                       // Simulation Parameter (Count)  ES% ET% EG%             // Earth Unit Percentages  AS% AM% AD%             // Alien Unit Percentages  Prob                    // Probability of generation per timestep  MinP MaxP MinH MaxH MinC MaxC  // Earth Ranges: Power, Health, Capacity  MinP MaxP MinH MaxH MinC MaxC  // Alien Ranges: Power, Health, Capacity   `

5\. Project Structure
---------------------

### Core Systems

*   **RandGen.h/cpp**: Handles random number generation and unit creation logic.
    
*   **EarthArmy.h/cpp**: Container class managing ES, ET, and EG lists13131313.
    
*   **AlienArmy.h/cpp**: Container class managing AS, AM, and AD lists14.
    

### Unit Classes

*   **Base:** Unit.h / Unit.cpp (Abstract Base Class).
    
*   **Earth:** ES (Soldier), ET (Tank), EG (Gunner).
    
*   **Alien:** AS (Soldier), AM (Monster), AD (Drone)151515151515151515.
    

### Utility & Interfaces

*   **Interfaces:** StackADT.h, QueueADT.h.
    
*   **Nodes:** Node.h (Standard), priNode.h (Priority)16.
    

6\. How to Build
----------------

The project is configured as a Visual Studio Solution (.vcxproj).

1.  **Requirements:** Visual Studio with C++ workload installed.
    
2.  **Setup:** Open Phase1.2code.vcxproj17.
    
3.  **Build:** Select **Build > Build Solution** (or press Ctrl+Shift+B).
    
4.  **Run:** Ensure a valid input text file is in the directory and run the executable.
    

Alien Invasion: Battle Simulation

1\. Project Overview
--------------------

This project is a C++ Object-Oriented simulation engine designed to model a battlefield conflict between an **Earth Army** and an **Alien Army**. The simulation operates in discrete time steps, generating units based on probabilistic inputs and managing them using custom-built Abstract Data Types (ADTs).

The primary goal of the application is to simulate unit generation, storage in specific data structures based on unit type, and eventually combat logic (Phase 1 currently covers generation and storage).

2\. Army Architecture & Unit Types
----------------------------------

The simulation distinguishes between two armies, each containing three specific unit types. Each unit type is managed by a distinct Data Structure chosen to represent its behavior on the battlefield.

All units inherit from the abstract base class Unit.

### 🌍 Earth Army

**Unit TypeClassDescriptionData StructureLogic & SourceEarth Soldier**ESStandard Infantry**LinkedQueue**

Deployed in FIFO (First-In, First-Out) order11.

**Earth Tank**ETHeavy Armor**ArrayStack**

Maintained in LIFO (Last-In, First-Out) order; newest tanks deploy first22.

**Earth Gunner**EGHigh Damage**priQueue**

**Priority Queue**. Priority is calculated as $\\sqrt{Health \\times Power}$, ensuring stronger units act first33.

### 👽 Alien Army

**Unit TypeClassDescriptionData StructureLogic & SourceAlien Soldier**ASStandard Infantry**LinkedQueue**

FIFO deployment4.

**Alien Monster**AMHeavy Unit**ArrayPointers**

Managed via a dynamic array of pointers for direct/random access5.

**Alien Drone**ADAerial/Fast**DoubleQueue**

A double-ended queue allowing simultaneous attacks from the front and rear6.

3\. Custom Data Structures (ADTs)
---------------------------------

The project implements template-based Data Structures from scratch to manage the units.

*   **LinkedQueue**: A standard Queue implementation using a linked list (FIFO)77.
    
*   **ArrayStack**: A Stack implementation using a static array (LIFO)8.
    

*   **priQueue**: A Priority Queue implemented as a sorted linked list.
    
    *   _Implementation:_ Uses priNode which stores a priority integer. The enqueue method uses insertion sort logic to place high-priority nodes at the head.
        
*   **ArrayPointers**: A custom container managing a dynamic array of pointers, specifically designed for AM units10101010.
    

4\. Simulation Flow & Input
---------------------------

### Random Generation (RandGen)

The RandGen class handles the creation of units based on configuration:

1.  **Probability Check:** A global probability (prob) determines if _any_ unit is generated at a specific timestep.
    
2.  **Type Selection:** If generation occurs, random percentages determine if the unit is a Soldier, Tank/Monster, or Gunner/Drone.
    
3.  **Stat Randomization:** Health, Power, and Attack Capacity are randomized within min/max ranges provided in the input file.
    

### Input File Format

The Game::ReadInput function parses a text file to configure the simulation. The expected format is11:

Plaintext

Plain textANTLR4BashCC#CSSCoffeeScriptCMakeDartDjangoDockerEJSErlangGitGoGraphQLGroovyHTMLJavaJavaScriptJSONJSXKotlinLaTeXLessLuaMakefileMarkdownMATLABMarkupObjective-CPerlPHPPowerShell.propertiesProtocol BuffersPythonRRubySass (Sass)Sass (Scss)SchemeSQLShellSwiftSVGTSXTypeScriptWebAssemblyYAMLXML`   N                       // Simulation Parameter (Count)  ES% ET% EG%             // Earth Unit Percentages  AS% AM% AD%             // Alien Unit Percentages  Prob                    // Probability of generation per timestep  MinP MaxP MinH MaxH MinC MaxC  // Earth Ranges: Power, Health, Capacity  MinP MaxP MinH MaxH MinC MaxC  // Alien Ranges: Power, Health, Capacity   `

5\. Project Structure
---------------------

### Core Systems

*   **RandGen.h/cpp**: Handles random number generation and unit creation logic.
    
*   **EarthArmy.h/cpp**: Container class managing ES, ET, and EG lists13131313.
    
*   **AlienArmy.h/cpp**: Container class managing AS, AM, and AD lists14.
    

### Unit Classes

*   **Base:** Unit.h / Unit.cpp (Abstract Base Class).
    
*   **Earth:** ES (Soldier), ET (Tank), EG (Gunner).
    
*   **Alien:** AS (Soldier), AM (Monster), AD (Drone)151515151515151515.
    

### Utility & Interfaces

*   **Interfaces:** StackADT.h, QueueADT.h.
    
*   **Nodes:** Node.h (Standard), priNode.h (Priority)16.
    

6\. How to Build
----------------

The project is configured as a Visual Studio Solution (.vcxproj).

1.  **Requirements:** Visual Studio with C++ workload installed.
    
2.  **Setup:** Open Phase1.2code.vcxproj17.
    
3.  **Build:** Select **Build > Build Solution** (or press Ctrl+Shift+B).
    
4.  **Run:** Ensure a valid input text file is in the directory and run the executable.