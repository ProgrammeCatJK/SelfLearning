# Knowledge Graph

## What is a Knowledge Graph?
A **Knowledge Graph (KG)** is a way to represent information as **nodes** and **relationships (edges)**.  

Basic structure:  
```
N —<E>— N
```

- **N** = Node (entity or concept)  
- **E** = Edge (relationship connecting nodes)  

---

## Example

```
Ottawa — Capital — Canada
```

- Ottawa is a node  
- Canada is a node  
- “Capital” is the edge connecting them  

> Nodes can have **multiple edges**, representing different relationships.

---

## Example in Healthcare

```
Patient —<Consults>— Provider
Patient —<ReceivesSupport>— HealthcareSupportLine
```

- Enables systems to provide **precise, context-aware information**  
- Relationships capture meaningful connections between entities  

---

## GraphRAG vs Traditional RAG

| Feature                | GraphRAG                        | Traditional RAG              |
|------------------------|---------------------------------|-----------------------------|
| Accuracy               | Higher                          | Moderate                     |
| Maintainability        | Easier                          | Harder                       |
| Query explainability   | Traceable / Explainable         | Not explicit                 |
| Data structure         | Structured graph                | Unstructured documents       |

> GraphRAG improves retrieval by leveraging structured relationships, making answers more accurate and traceable.

---

## NaLLM Demo

- **Use Case:** Unstructured data import  
- Shows how knowledge graphs can help **organize and query information efficiently**  

---

## Key Takeaways

- Knowledge Graph = Nodes + Relationships  
- Enables **explainable and precise queries**  
- GraphRAG is an improvement over traditional RAG for structured data  
- Useful for domains like **healthcare, finance, and enterprise data**