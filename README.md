<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script> <script type="module"> Array.from(document.getElementsByClassName("language-mermaid")).forEach(el => { el.classList.add("mermaid"); }); import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11.4.1/dist/mermaid.esm.min.mjs'; mermaid.initialize({ startOnLoad: true, theme: 'light' }); </script>
# Economic Load Dispatch main doc

### Algorithm

1. **Start**  
   Initialize all required variables and data structures.

2. **Input Generator Data**  
   - For each generator:
     - Read min & max capacities
     - Read cost coefficients: a, b, c

3. **Input User Requirements**  
   - Read total power demand  
   - Set tolerance for acceptable error  
   - Set maximum number of iterations

4. **Initialize Lambda**  
   Set an initial value for lambda (e.g. 0.0)

5. **Repeat Until Convergence or Max Iteration**  
   For each iteration:
   - For each generator:
     - Compute power using lambda and cost coefficients
     - Clamp power within [min_capacity, max_capacity]
   - Calculate total generated power
   - Check if $|total_power - demand| < tolerance$:
     - If yes, exit loop (converged)
     - Else, adjust lambda based on error

6. **Output Results**  
   - Final lambda value  
   - Power output for each generator  
   - Total cost (optional)

7. **End**


### Flowchart

```mermaid
flowchart TD
   A[Start] --> B[Initialize variables and data structures]
   B --> C[Input Generator Data]
   C --> D["Read min & max capacities and cost coefficients (a, b, c)"]
   D --> E[Input User Requirements]
   E --> F[Read total power demand, tolerance, max iterations]
   F --> G["Initialize Lambda (e.g. λ = 0.0)"]
   G --> H{Repeat Until Converged or Max Iterations}
   
   H --> I[For each generator:<br>Compute power using λ and cost coefficients]
   I --> J[Clamp power within min & max limits]
   J --> K[Calculate total generated power]
   K --> L{"Is |Total Power - Demand| < Tolerance?"}
   
   L -- Yes --> M["Converged: Exit Loop"]
   L -- No --> N[Adjust Lambda based on error]
   N --> H

   M --> O[Output Results:<br>Final λ, Generator Outputs, Total Cost]
   O --> P[End]

```
