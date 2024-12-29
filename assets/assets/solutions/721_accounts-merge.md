# Accounts Merge

## Problem Statement

Given a list of accounts where each element `accounts[i]` is a list of strings, where the first element `accounts[i][0]` is the name of the account owner, and the rest of the elements are emails representing the account. Merge accounts such that each account belongs to the same person if there is some common email.

Return the accounts in the following format: the first element of each account is the name, and the rest of the elements are emails in sorted order. The accounts themselves can be returned in any order.

## Input

```text
accounts = [
    ["John", "johnsmith@mail.com", "john00@mail.com"],
    ["John", "johnnybravo@mail.com"],
    ["John", "johnsmith@mail.com", "john_newyork@mail.com"],
    ["Mary", "mary@mail.com"]
]
```

## Output

```text
[
    ["John", "john00@mail.com", "john_newyork@mail.com", "johnsmith@mail.com"],
    ["John", "johnnybravo@mail.com"],
    ["Mary", "mary@mail.com"]
]
```

## Solutions

### Dart

```dart
class UnionFind {
  List<int> parent;

  UnionFind(int size) : parent = List.generate(size, (index) => index);

  int find(int x) {
    if (parent[x] != x) {
      parent[x] = find(parent[x]);
    }
    return parent[x];
  }

  void union(int x, int y) {
    parent[find(x)] = find(y);
  }
}

List<List<String>> accountsMerge(List<List<String>> accounts) {
  final emailToId = <String, int>{};
  final emailToName = <String, String>{};
  int id = 0;

  for (var account in accounts) {
    String name = account[0];
    for (int i = 1; i < account.length; i++) {
      String email = account[i];
      if (!emailToId.containsKey(email)) {
        emailToId[email] = id++;
        emailToName[email] = name;
      }
    }
  }

  final uf = UnionFind(id);

  for (var account in accounts) {
    int firstId = emailToId[account[1]]!;
    for (int i = 2; i < account.length; i++) {
      uf.union(firstId, emailToId[account[i]]!);
    }
  }

  final merged = <int, List<String>>{};
  emailToId.forEach((email, id) {
    int rootId = uf.find(id);
    merged.putIfAbsent(rootId, () => []).add(email);
  });

  return merged.values
      .map((emails) {
        emails.sort();
        String name = emailToName[emails.first]!;
        return [name, ...emails];
      })
      .toList();
}
```

### C#

```csharp
public class Solution {
    public IList<IList<string>> AccountsMerge(IList<IList<string>> accounts) {
        var emailToId = new Dictionary<string, int>();
        var emailToName = new Dictionary<string, string>();
        int id = 0;

        foreach (var account in accounts) {
            string name = account[0];
            for (int i = 1; i < account.Count; i++) {
                string email = account[i];
                if (!emailToId.ContainsKey(email)) {
                    emailToId[email] = id++;
                    emailToName[email] = name;
                }
            }
        }

        var uf = new UnionFind(id);

        foreach (var account in accounts) {
            int firstId = emailToId[account[1]];
            for (int i = 2; i < account.Count; i++) {
                uf.Union(firstId, emailToId[account[i]]);
            }
        }

        var merged = new Dictionary<int, List<string>>();
        foreach (var email in emailToId.Keys) {
            int rootId = uf.Find(emailToId[email]);
            if (!merged.ContainsKey(rootId)) {
                merged[rootId] = new List<string>();
            }
            merged[rootId].Add(email);
        }

        var result = new List<IList<string>>();
        foreach (var emails in merged.Values) {
            emails.Sort();
            string name = emailToName[emails[0]];
            emails.Insert(0, name);
            result.Add(emails);
        }

        return result;
    }

    private class UnionFind {
        private int[] parent;

        public UnionFind(int size) {
            parent = new int[size];
            for (int i = 0; i < size; i++) {
                parent[i] = i;
            }
        }

        public int Find(int x) {
            if (parent[x] != x) {
                parent[x] = Find(parent[x]);
            }
            return parent[x];
        }

        public void Union(int x, int y) {
            parent[Find(x)] = Find(y);
        }
    }
}
```

### Java

```java
class Solution {
    public List<List<String>> accountsMerge(List<List<String>> accounts) {
        Map<String, Integer> emailToId = new HashMap<>();
        Map<String, String> emailToName = new HashMap<>();
        int id = 0;

        for (List<String> account : accounts) {
            String name = account.get(0);
            for (int i = 1; i < account.size(); i++) {
                String email = account.get(i);
                if (!emailToId.containsKey(email)) {
                    emailToId.put(email, id++);
                    emailToName.put(email, name);
                }
            }
        }

        UnionFind uf = new UnionFind(id);

        for (List<String> account : accounts) {
            int firstId = emailToId.get(account.get(1));
            for (int i = 2; i < account.size(); i++) {
                uf.union(firstId, emailToId.get(account.get(i)));
            }
        }

        Map<Integer, List<String>> merged = new HashMap<>();
        for (String email : emailToId.keySet()) {
            int rootId = uf.find(emailToId.get(email));
            merged.computeIfAbsent(rootId, x -> new ArrayList<>()).add(email);
        }

        List<List<String>> result = new ArrayList<>();
        for (List<String> emails : merged.values()) {
            Collections.sort(emails);
            String name = emailToName.get(emails.get(0));
            List<String> account = new ArrayList<>();
            account.add(name);
            account.addAll(emails);
            result.add(account);
        }

        return result;
    }

    private class UnionFind {
        private int[] parent;

        public UnionFind(int size) {
            parent = new int[size];
            for (int i = 0; i < size; i++) {
                parent[i] = i;
            }
        }

        public int find(int x) {
            if (parent[x] != x) {
                parent[x] = find(parent[x]);
            }
            return parent[x];
        }

        public void union(int x, int y) {
            parent[find(x)] = find(y);
        }
    }
}
```

### Swift

```swift
class Solution {
    func accountsMerge(_ accounts: [[String]]) -> [[String]] {
        var emailToId = [String: Int]()
        var emailToName = [String: String]()
        var id = 0

        for account in accounts {
            let name = account[0]
            for email in account[1...] {
                if emailToId[email] == nil {
                    emailToId[email] = id
                    emailToName[email] = name
                    id += 1
                }
            }
        }

        var uf = UnionFind(size: id)

        for account in accounts {
            let firstId = emailToId[account[1]]!
            for email in account[2...] {
                uf.union(firstId, emailToId[email]!)
            }
        }

        var merged = [Int: [String]]()
        for (email, id) in emailToId {
            let rootId = uf.find(id)
            merged[rootId, default: []].append(email)
        }

        var result = [[String]]()
        for emails in merged.values {
            let sortedEmails = emails.sorted()
            let name = emailToName[sortedEmails[0]]!
            result.append([name] + sortedEmails)
        }

        return result
    }

    private class UnionFind {
        private var parent: [Int]

        init(size: Int) {
            parent = Array(0..<size)
        }

        func find(_ x: Int) -> Int {
            if parent[x] != x {
                parent[x] = find(parent[x])
            }
            return parent[x]
        }

        func union(_ x: Int, _ y: Int) {
            parent[find(x)] = find(y)
        }
    }
}
```

### The End

