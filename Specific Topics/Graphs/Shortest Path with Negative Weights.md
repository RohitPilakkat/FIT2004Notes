What is the shortest distance from S to X in a graph with negative weights?

- If we use [[Dijkstra's Algorithm]] on this graph, we won't be able to handle this scenario because of the negative weights. Dijkstra's is a greedy algorithm where it will always take the greediest choice that attains the best solution to reach the current node. Say we have a negative edge somewhere later that reduces the weighting of the travel. This edge would not be accessible anymore if there was a previous edge that outweighed an alternate shorter edge and therefore is never traversed. 

Instead we can use [[Bellman-Ford Algorithm]]
