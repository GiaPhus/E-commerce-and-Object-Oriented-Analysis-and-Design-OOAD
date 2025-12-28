# E-commerce-and-Object-Oriented-Analysis-and-Design-OOAD-
Project Description:

Title: E-commerce and Object-Oriented Analysis and Design (OOAD)

Overview:
The project delved into the realms of E-commerce and Object-Oriented Analysis and Design (OOAD), two pivotal aspects shaping contemporary business landscapes. Through rigorous exploration and study, the project sought to understand and implement principles, methodologies, and technologies associated with E-commerce platforms and OOAD strategies.

Highlights:

    E-commerce Exploration:
        Defined E-Business and E-Commerce concepts, delineating their key components, characteristics, advantages, and disadvantages.
        Investigated various forms of E-Marketing and E-Payment, elucidating their significance and prevalent applications.
        Explored popular E-commerce platforms in Vietnam, highlighting their operational models and differences from traditional business paradigms.

    Introduction to Odoo:
        Provided an overview of Odoo, delineating its functionalities and reasons for adoption.
        Explored the business modules within Odoo, emphasizing their roles and integration into E-commerce frameworks.
        Discussed specific modules such as Accounting and Finance, CRM, Purchase Management, Inventory Management, HRM, Point of Sale, Website, and Project Management, outlining their core functionalities and applications in E-commerce scenarios.

    OOAD Insights:
        Applied Object-Oriented Analysis and Design methodologies to analyze and design systems.
        Employed principles such as encapsulation, inheritance, and polymorphism to model and represent real-world entities and their interactions within an E-commerce context.
        Utilized UML diagrams, including class diagrams, sequence diagrams, and use case diagrams, to visualize system structures and behaviors, facilitating effective design and implementation.

Key Learning:

    Enhanced understanding of E-commerce ecosystems, including business models, marketing strategies, payment systems, and platform functionalities.
    Proficiency in utilizing Odoo for business management, encompassing various modules tailored for E-commerce operations.
    Practical application of Object-Oriented Analysis and Design principles to conceptualize, model, and develop scalable and maintainable software systems for E-commerce ventures.


```mermaid
flowchart TD
    A[Raw CSV Inputs] -->|Read CSV| B[Staging Layer]

    B -->|Parse datetime<br/>Validate required fields| C[Orders After DQ]
    C -->|Deduplicate by order_id<br/>Keep latest ingested_at| D[Valid Orders]

    B -->|Validate quantity & price| E[Items After DQ]
    E -->|Reject orphan items| F[Valid Items]

    D -->|Filter completed orders| G[Completed Orders]
    F -->|Join| G

    G -->|Aggregate| H[Daily Revenue Mart]

    C --> I[Rejected Orders]
    E --> J[Rejected Items]

    H --> K[daily_revenue.csv]
    I --> L[rejected_orders.csv]
    J --> M[rejected_items.csv]
    H --> N[quality_report.json]
