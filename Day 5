#### Brief overview
Introduction to Maze Routing – Lee’s Algorithm
Maze routing is a pathfinding algorithm used in VLSI design to find an optimal connection between two points in a circuit. Lee’s Algorithm is a classic maze-routing method that guarantees finding the shortest path if one exists.

Steps of Lee’s Algorithm:

Grid Representation: The circuit layout is divided into a grid where obstacles are marked as blocked.
Breadth-First Expansion: Starting from the source, neighboring cells are assigned increasing distance values.
Backtracking for Path Extraction: Once the destination is reached, the shortest path is traced back by following the decreasing values.
Optimization: The route is smoothed to avoid unnecessary detours.
Advantages:

Guarantees finding a path if one exists.
Finds the shortest path.
Disadvantages:

High memory and runtime complexity for large designs.
Lee’s Algorithm Conclusion
Lee’s Algorithm is useful in small routing problems but becomes computationally expensive for larger circuits. It forms the foundation for modern routing algorithms like A search and pattern-based routing*. Enhancements such as rip-up and re-route, hierarchical routing, and multi-layer routing improve its efficiency for real-world VLSI applications.

Design Rule Check (DRC)
Design Rule Check (DRC) ensures that the physical layout of a circuit follows manufacturing constraints. These rules prevent defects and improve yield.

Common DRC Rules:

Width Rules: Minimum width for metal traces to ensure manufacturability.
Spacing Rules: Minimum distance between wires to prevent short circuits.
Enclosure Rules: Via enclosures must have sufficient overlap.
Antenna Rules: Prevent damage due to charge accumulation during fabrication.
DRC is performed using tools like Magic, Calibre, or TritonRoute to identify violations and correct them before fabrication.

Basics of Global and Detail Routing and Configuring TritonRoute
Routing is divided into global routing and detailed routing:

Global Routing:

Divides the layout into coarse routing regions.
Determines approximate paths for interconnects.
Ensures congestion is minimized.
Tools: FastRoute, TritonRoute.
Detailed Routing:

Assigns exact tracks and vias for interconnections.
Ensures compliance with DRC rules.
Uses advanced techniques like rip-up and re-route, layer assignment, and via optimization.
Tools: TritonRoute, NanoRoute.
Configuring TritonRoute:

Define routing constraints such as metal layer usage and design rules.
Provide pre-processed route guides for guided routing.
Run TritonRoute to generate a legal routed design.
TritonRoute Feature 1 - Honors Pre-Processed Route Guides
TritonRoute follows pre-generated route guides to ensure optimal routing and avoid congestion.

How it works:

Route guides are generated during global routing.
TritonRoute uses these guides to create an initial routing solution.
Prevents excessive detouring and improves routing efficiency.
This feature helps in achieving DRC-clean routing without excessive iterations.

TritonRoute Feature 2 & 3 - Inter-Guide Connectivity and Intra- & Inter-Layer Routing
Inter-guide connectivity ensures smooth transitions between different routing guides.
Intra-layer routing assigns tracks within the same metal layer.
Inter-layer routing optimizes via placement and layer transitions to reduce congestion.
TritonRoute intelligently adjusts routing paths to maintain connectivity while minimizing resistance and delay.

TritonRoute Method to Handle Connectivity
TritonRoute ensures that all signal and power nets are correctly connected using techniques like:

Layer-based optimization: Choosing the best layer for each wire.
Short-path correction: Ensuring the shortest feasible path is taken.
Dynamic rerouting: Adjusting paths dynamically to resolve conflicts.
Antenna effect mitigation: Handling long wires to prevent charge buildup.
Routing Topology Algorithm and Final Files List Post-Route
After routing, TritonRoute generates files that describe the final layout:

DEF (Design Exchange Format): Stores placement and routing details.
GDS (Graphic Database System): Contains mask layout data for fabrication.
LEF (Library Exchange Format): Provides technology and standard cell info.
DRC Reports: Lists any violations that need correction.
The routing topology algorithm optimizes interconnects by:

Choosing efficient routing paths to reduce wirelength.
Minimizing via usage to improve reliability.
Ensuring manufacturability by following design rules.

## Thanks for this opportunity I can make it till Day 3 only and explanation of day 4 and 5, I always wanted to learn something new and this course made me do it. Hope you will like it

# END
