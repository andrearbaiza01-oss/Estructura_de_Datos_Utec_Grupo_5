```mermaid
graph TD
    subgraph S1 [Bloque 1: Ingesta y Buffer]
        A["Stream de Entrada<br>(42.4M Registros E-commerce)"] --> B["Etapa 0: Ingesta & Buffer<br>(Cola FIFO Thread-Safe)"]
    end

    subgraph S2 [Bloque 2: Preprocesamiento]
        B --> C["Etapa 1: Preprocesamiento por Lotes<br>(Ordenamiento Merge Sort & Búsqueda Binaria)"]
    end

    subgraph S3 [Bloque 3: Priorización]
        C --> D["Etapa 2: Cola con Prioridades<br>(Min/Max-Heap para Pagos y Fraude)"]
    end

    subgraph S4 [Bloque 4: Almacenamiento y Lookup]
        D --> E["Etapa 3: Almacenamiento & Caché<br>(Hash Table & LRU Cache O(1))"]
    end

    subgraph S5 [Bloque 5: Indexación en Disco]
        E --> F["Etapa 4: Indexación Principal<br>(B+Tree para Consultas por Rango O(log N))"]
    end

    subgraph S6 [Bloque 6: Espacio Multidimensional]
        F --> G["Etapa 5: Índice Multidimensional<br>(R-Tree vs. KNN Exacto / Fuerza Bruta)"]
    end

    subgraph S7 [Bloque 7: Investigación Avanzada - Fijas]
        G --> H["Etapa 6 [FIJA]: Filtrado Probabilístico<br>(Bloom Filter & Count-Min Sketch)"]
        H --> I["Etapa 7 [FIJA]: Similitud Aproximada<br>(MinHash+LSH & HNSW / ANN)"]
    end

    subgraph S8 [Bloque 8: Análisis de Grafos - Fijas]
        I --> J["Etapa 8 [FIJA]: Grafo de Dominio<br>(PageRank & Louvain/Leiden Communities)"]
    end

    subgraph S9 [Bloque Transversal: Servicio y Visualización]
        J --> K["Etapa 9: Servicio y Visualización<br>(Top-K Heap, Trie Autocomplete & Dashboard)"]
    end

    %% Conexiones observables de retroalimentación y flujo
    H -.->|Alertas de Fraude| K
    I -.->|Recomendaciones| K
    J -.->|Insights de Co-compra| K