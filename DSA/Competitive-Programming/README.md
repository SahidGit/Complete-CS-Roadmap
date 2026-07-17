# 🏆 Competitive Programming (CP) Reference

Competitive Programming combines mathematical logic, algorithm speed, and layout speed under strict time and memory limits.

---

## 💻 Platforms

- **Codeforces**: The premier platform for algorithm contests. Follows a division rating system (Div 1, Div 2, Div 3, Div 4).
- **AtCoder**: High-quality algorithmic math problems based in Japan.
- **CodeChef**: Long and short format contests, highly popular for beginners.

---

## ⚡ C++ Fast I/O Template
Always include fast standard input/output streams configurations in your CP solutions:

```cpp
#include <bits/stdc++.h>
using namespace std;

#define fast_io ios_base::sync_with_stdio(false); cin.tie(NULL); cout.tie(NULL)
#define ll long long
#define pb push_back
#define mp make_pair
#define vi vector<int>
#define vll vector<ll>

void solve() {
    // Write your solution here
}

int main() {
    fast_io;
    int t;
    cin >> t;
    while(t--) {
        solve();
    }
    return 0;
}
```

---

## 📈 Contest Strategies
1. **Read all problems quickly**: Do not get stuck on Problem A if Problem B is an implementation task you can code in 2 minutes.
2. **Analyze Constraints**:
   - $N \le 10^5 \implies O(N \log N)$ or $O(N)$ solution required.
   - $N \le 100 \implies O(N^3)$ is acceptable.
   - $N \le 20 \implies O(2^N)$ backtracking/state compression acceptable.
3. **Use Offline Stress Testing**: Write a slow, correct brute-force script to cross-validate results against your fast optimized algorithm using a random test generator script.

---

## 🔗 Platform Links
- [Codeforces](https://codeforces.com/)
- [AtCoder](https://atcoder.jp/)
- [CodeChef](https://www.codechef.com/)
