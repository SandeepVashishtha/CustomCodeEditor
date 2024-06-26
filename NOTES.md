## Python3 Code:

Business case problem: calculating the total revenue from a list of sales transactions.

```
def calculate_total_revenue(sales):
    total_revenue = 0
    for item, price in sales:
        total_revenue += price
    return total_revenue
```

### Example usage: This would be given as inputs

```
sales = [("Product A", 10), ("Product B", 20), ("Product C", 15)]
total_revenue = calculate_total_revenue(sales)
print("Total Revenue:", total_revenue)
```

## Javascript Code:

Shortest path between multiple locations on a map

```
function calculateTotalDistance(locations) {
    // Helper function to calculate distance between two points (using Euclidean distance for simplicity)
    function distance(point1, point2) {
        return Math.sqrt(Math.pow(point2.x - point1.x, 2) + Math.pow(point2.y - point1.y, 2));
    }

    // Helper function to calculate total distance of a route
    function routeDistance(route) {
        let totalDistance = 0;
        for (let i = 0; i < route.length - 1; i++) {
            totalDistance += distance(locations[route[i]], locations[route[i + 1]]);
        }
        return totalDistance;
    }

    // Generate all possible permutations of routes
    function* permutations(arr) {
        if (arr.length === 1) {
            yield arr;
        } else {
            for (let i = 0; i < arr.length; i++) {
                const rest = [...arr.slice(0, i), ...arr.slice(i + 1)];
                for (const perm of permutations(rest)) {
                    yield [arr[i], ...perm];
                }
            }
        }
    }

    // Find the shortest route among all permutations
    let shortestDistance = Infinity;
    let shortestRoute = null;
    for (const perm of permutations([...Array(locations.length).keys()])) {
        const dist = routeDistance(perm);
        if (dist < shortestDistance) {
            shortestDistance = dist;
            shortestRoute = perm;
        }
    }

    return shortestDistance;
}
```

### Example usage: Would be passed as inputs

```
const locations = [
    { x: 0, y: 0 },
    { x: 1, y: 2 },
    { x: 3, y: 1 },
    { x: 2, y: 3 }
];

const totalDistance = calculateTotalDistance(locations);
console.log("Total Distance in meters:", totalDistance);
```
