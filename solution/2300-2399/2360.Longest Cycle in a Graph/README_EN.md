# [2360. Longest Cycle in a Graph](https://leetcode.com/problems/longest-cycle-in-a-graph)

[中文文档](/solution/2300-2399/2360.Longest%20Cycle%20in%20a%20Graph/README.md)

## Description

<p>You are given a <strong>directed</strong> graph of <code>n</code> nodes numbered from <code>0</code> to <code>n - 1</code>, where each node has <strong>at most one</strong> outgoing edge.</p>

<p>The graph is represented with a given <strong>0-indexed</strong> array <code>edges</code> of size <code>n</code>, indicating that there is a directed edge from node <code>i</code> to node <code>edges[i]</code>. If there is no outgoing edge from node <code>i</code>, then <code>edges[i] == -1</code>.</p>

<p>Return <em>the length of the <strong>longest</strong> cycle in the graph</em>. If no cycle exists, return <code>-1</code>.</p>

<p>A cycle is a path that starts and ends at the <strong>same</strong> node.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/2300-2399/2360.Longest%20Cycle%20in%20a%20Graph/images/graph4drawio-5.png" style="width: 335px; height: 191px;" />
<pre>
<strong>Input:</strong> edges = [3,3,4,2,3]
<strong>Output:</strong> 3
<strong>Explanation:</strong> The longest cycle in the graph is the cycle: 2 -&gt; 4 -&gt; 3 -&gt; 2.
The length of this cycle is 3, so 3 is returned.
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://fastly.jsdelivr.net/gh/doocs/leetcode@main/solution/2300-2399/2360.Longest%20Cycle%20in%20a%20Graph/images/graph4drawio-1.png" style="width: 171px; height: 161px;" />
<pre>
<strong>Input:</strong> edges = [2,-1,3,1]
<strong>Output:</strong> -1
<strong>Explanation:</strong> There are no cycles in this graph.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == edges.length</code></li>
	<li><code>2 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>-1 &lt;= edges[i] &lt; n</code></li>
	<li><code>edges[i] != i</code></li>
</ul>


## Solutions

<!-- tabs:start -->

### **Python3**

```python
class Solution:
    def longestCycle(self, edges: List[int]) -> int:
        n = len(edges)
        vis = [False] * n
        ans = -1
        for i in range(n):
            if vis[i]:
                continue
            curr = i
            cycle = []
            while curr != -1 and not vis[curr]:
                vis[curr] = True
                cycle.append(curr)
                curr = edges[curr]
            if curr == -1:
                continue
            for j, v in enumerate(cycle):
                if v == curr:
                    ans = max(ans, len(cycle) - j)
                    break
        return ans
```

### **Java**

```java
class Solution {
    public int longestCycle(int[] edges) {
        int n = edges.length;
        boolean[] vis = new boolean[n];
        int ans = -1;
        for (int i = 0; i < n; ++i) {
            if (vis[i]) {
                continue;
            }
            int curr = i;
            List<Integer> cycle = new ArrayList<>();
            while (curr != -1 && !vis[curr]) {
                cycle.add(curr);
                vis[curr] = true;
                curr = edges[curr];
            }
            if (curr == -1) {
                continue;
            }
            for (int j = 0; j < cycle.size(); ++j) {
                if (cycle.get(j) == curr) {
                    ans = Math.max(ans, cycle.size() - j);
                    break;
                }
            }
        }
        return ans;
    }
}
```

### **C++**

```cpp
class Solution {
public:
    int longestCycle(vector<int>& edges) {
        int n = edges.size();
        vector<int> vis(n);
        int ans = -1;
        for (int i = 0; i < n; ++i)
        {
            if (vis[i]) continue;
            int curr = i;
            vector<int> cycle;
            while (curr != -1 && !vis[curr])
            {
                cycle.push_back(curr);
                vis[curr] = true;
                curr = edges[curr];
            }
            if (curr == -1) continue;
            for (int j = 0; j < cycle.size(); ++j)
            {
                if (cycle[j] == curr)
                {
                    ans = max(ans, (int) cycle.size() - j);
                    break;
                }
            }
        }
        return ans;
    }
};
```

### **Go**

```go
func longestCycle(edges []int) int {
	n := len(edges)
	vis := make([]bool, n)
	ans := -1
	for i := range edges {
		if vis[i] {
			continue
		}
		curr := i
		cycle := []int{}
		for curr != -1 && !vis[curr] {
			cycle = append(cycle, curr)
			vis[curr] = true
			curr = edges[curr]
		}
		if curr == -1 {
			continue
		}
		for j, v := range cycle {
			if v == curr {
				ans = max(ans, len(cycle)-j)
				break
			}
		}
	}
	return ans
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}
```

### **TypeScript**

```ts

```

### **...**

```

```

<!-- tabs:end -->
