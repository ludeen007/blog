+++
title = "深度探索C++对象模型"
categories = ["C++"]
tags = ["C++", "cheat-sheet"]
date = 2020-03-08T08:53:09+08:00
+++

## Contents of Inside the C++ Object Model

### 1. Object Lessons

    Layout Costs for Adding Encapsulation
    1.1. The C++ Object Model
        A Simple Object Model
        A Table-driven Object Model
        The C++ Object Model
            Adding Inheritance
        How the Object Model Effects Programs
    1.2. A Keyword Distinction
        Keywords, Schmeewords
        The Politically Correct Struct
    1.3. An Object Distinction
        The Type of a Pointer
        Adding Polymorphism

### 2. The Semantics of Constructors

    2.1. Default Constructor Construction
        Member Class Object with Default Constructor
        Base Class with Default Constructor
        Class with a Virtual Function
        Class with a Virtual Base Class
        Summary
    2.2. Copy Constructor Construction
        Default Memberwise Initialization
        Bitwise Copy Semantics
        Bitwise Copy Semantics—Not!
        Resetting the Virtual Table Pointer
        Handling the Virtual Base Class Subobject
    2.3. Program Transformation Semantics
        Explicit Initialization
        Argument Initialization
        Return Value Initialization
        Optimization at the User Level
        Optimization at the Compiler Level
        The Copy Constructor: To Have or To Have Not?
        Summary
    2.4. Member Initialization List

### 3. The Semantics of Data

    3.1. The Binding of a Data Member
    3.2. Data Member Layout
    3.3. Access of a Data Member
        Static Data Members
        Nonstatic Data Members
    3.4. Inheritance and the Data Member
        Inheritance without Polymorphism
        Adding Polymorphism
        Multiple Inheritance
        Virtual Inheritance
    3.5. Object Member Efficiency
    3.6. Pointer to Data Members
        Efficiency of Pointers to Members

### 4. The Semantics of Function

    4.1. Varieties of Member Invocation
        Nonstatic Member Functions
            Name Mangling
        Virtual Member Functions
        Static Member Functions
    4.2. Virtual Member Functions
        Virtual Functions under MI
        Virtual Functions under Virtual Inheritance
    4.3. Function Efficiency
    4.4. Pointer-to-Member Functions
        Supporting Pointer-to-Virtual-Member Functions
        Pointer-to-Member Functions under MI
        Pointer-to-Member Efficiency
    4.5. Inline Functions
        Formal Arguments
        Local Variables

### 5. Semantics of Construction, Destruction, and Copy

    Presence of a Pure Virtual Destructor
    Presence of a Virtual Specification
    Presence of const within a Virtual Specification
    A Reconsidered Class Declaration
    5.1. Object Construction without Inheritance
        Abstract Data Type
        Preparing for Inheritance
    5.2. Object Construction under Inheritance
        Virtual Inheritance
        The Semantics of the vptr Initialization
    5.3. Object Copy Semantics
    5.4. Object Efficiency
    5.5. Semantics of Destruction

### 6. Runtime Semantics

    6.1. Object Construction and Destruction
        Global Objects
        Local Static Objects
        Arrays of Objects
        Default Constructors and Arrays
    6.2. Operators new and delete
        The Semantics of new Arrays
        The Semantics of Placement Operator new
    6.3. Temporary Objects
        A Temporary Myth

### 7. On the Cusp of the Object Model

    7.1. Templates
        Template Instantiation
        Error Reporting within a Template
        Name Resolution within a Template
        Member Function Instantiation
    7.2. Exception Handling
        A Quick Review of Exception Handling
        Exception Handling Support
            Determine if the Throw Occurred within a try Block
            Compare the Type of the Exception against the Type of Each Catch Clause
            What Happens When an Actual Object Is Thrown during Program Execution?
    7.3. Runtime Type Identification
        Introducing a Type-Safe Downcast
        A Type-Safe Dynamic Cast
        References Are Not Pointers
        Typeid Operator
    7.4. Efficient, but Inflexible?
        Dynamic Shared Libraries
        Shared Memory
