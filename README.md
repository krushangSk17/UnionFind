# UnionFind

## code:

```python
class UnionFind:

    def __init__(self, n) -> None:
        self.parent = [i for i in range(n)]
        self.rank = [1]*n
    
    def find(self, a):
        if self.parent[a] != a:
            self.parent[a] = self.find(self.parent[a])
        return self.parent[a]

    def union(self, a, b):
        roota = self.find(a)
        rootb = self.find(b)

        if roota != rootb:
            if self.rank[roota] > self.rank[rootb]:
                self.parent[rootb] = roota
                self.rank[roota] += self.rank[rootb]
            elif self.rank[roota] < self.rank[rootb]:
                self.parent[roota] = rootb
                self.rank[rootb] += self.rank[roota]
            else:
                self.parent[rootb] = roota
                self.rank[roota] += self.rank[rootb]

    def size(self, a):
        roota = self.find(a)
        return self.rank[roota]
