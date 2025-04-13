```
import matplotlib.pyplot as plt
import networkx as nx

# Create a directed graph for the Quine-McCluskey method steps
G = nx.DiGraph()

# Add nodes for steps
G.add_node("Expression to Simplify", pos=(0, 5), color="blue")
G.add_node("Step 1: Minterms", pos=(0, 4), color="green")
G.add_node("Step 2: Group by 1's", pos=(-2, 3), color="orange")
G.add_node("Step 3: Prime Implicants", pos=(2, 3), color="orange")
G.add_node("Step 4: Implicant Chart", pos=(0, 2), color="purple")
G.add_node("Step 5: Essential Prime Implicants", pos=(0, 1), color="red")
G.add_node("Step 6: Final Expression", pos=(0, 0), color="gold")

# Add edges to represent progression
edges = [
    ("Expression to Simplify", "Step 1: Minterms"),
    ("Step 1: Minterms", "Step 2: Group by 1's"),
    ("Step 1: Minterms", "Step 3: Prime Implicants"),
    ("Step 2: Group by 1's", "Step 4: Implicant Chart"),
    ("Step 3: Prime Implicants", "Step 4: Implicant Chart"),
    ("Step 4: Implicant Chart", "Step 5: Essential Prime Implicants"),
    ("Step 5: Essential Prime Implicants", "Step 6: Final Expression"),
]

G.add_edges_from(edges)

# Draw the graph with positions and colors
pos = nx.get_node_attributes(G, 'pos')
colors = [data['color'] for _, data in G.nodes(data=True)]
nx.draw(
    G, 
    pos, 
    with_labels=True, 
    node_size=3000, 
    node_color=[G.nodes[n]['color'] for n in G.nodes],
    font_weight="bold", 
    font_size=10, 
    edge_color="black"
)

# Display the graph
plt.title("Quine-McCluskey Method Visualization", fontsize=14)
plt.show()

```
![[Pasted image 20250101231737.png]]
 