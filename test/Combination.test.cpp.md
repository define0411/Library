---
data:
  _extendedDependsOn:
  - icon: ':heavy_check_mark:'
    path: math/Combination.cpp
    title: Combination (nCk)
  - icon: ':question:'
    path: math/extgcd.cpp
    title: math/extgcd.cpp
  - icon: ':question:'
    path: math/modint.cpp
    title: mod int
  - icon: ':question:'
    path: template/template.cpp
    title: template/template.cpp
  _extendedRequiredBy: []
  _extendedVerifiedWith: []
  _pathExtension: cpp
  _verificationStatusIcon: ':heavy_check_mark:'
  attributes:
    '*NOT_SPECIAL_COMMENTS*': ''
    PROBLEM: https://onlinejudge.u-aizu.ac.jp/courses/library/7/DPL/5/DPL_5_E
    links:
    - https://onlinejudge.u-aizu.ac.jp/courses/library/7/DPL/5/DPL_5_E
  bundledCode: "#line 1 \"test/Combination.test.cpp\"\n#define PROBLEM \"https://onlinejudge.u-aizu.ac.jp/courses/library/7/DPL/5/DPL_5_E\"\
    \n\n#line 2 \"template/template.cpp\"\n#include <bits/stdc++.h>\nusing namespace\
    \ std;\n#define ll long long\n#define rep(i, n) for (int i = 0; i < n; i++)\n\
    #define REP(i, n) for (int i = 1; i < n; i++)\n#define rev(i, n) for (int i =\
    \ n - 1; i >= 0; i--)\n#define all(v) v.begin(), v.end()\n#define P pair<ll, ll>\n\
    #define len(s) (ll) s.size()\n\ntemplate <class T, class U>\ninline bool chmin(T\
    \ &a, U b) {\n    if (a > b) {\n        a = b;\n        return true;\n    }\n\
    \    return false;\n}\ntemplate <class T, class U>\ninline bool chmax(T &a, U\
    \ b) {\n    if (a < b) {\n        a = b;\n        return true;\n    }\n    return\
    \ false;\n}\nconstexpr ll inf = 3e18;\n#line 3 \"math/extgcd.cpp\"\n\nll extGCD(ll\
    \ a, ll b, ll &x, ll &y) {\n    if (!b) {\n        x = 1;\n        y = 0;\n  \
    \      return a;\n    }\n    ll d = extGCD(b, a % b, y, x);\n    y -= a / b *\
    \ x;\n    return d;\n}\n\nll modinv(ll a, ll m) {\n    ll x, y;\n    extGCD(a,\
    \ m, x, y);\n    return (x % m + m) % m;\n}\n#line 4 \"math/modint.cpp\"\n\ntemplate\
    \ <int MOD>\nstruct mint {\n    int32_t n;\n    mint() : n(0) {}\n    mint(ll\
    \ x) : n(x >= 0 ? x % MOD : (MOD - (-x) % MOD) % MOD) {}\n\n    mint &operator+=(const\
    \ mint &p) {\n        if ((n += p.n) >= MOD) n -= MOD;\n        return *this;\n\
    \    }\n    mint &operator-=(const mint &p) {\n        if ((n += MOD - p.n) >=\
    \ MOD) n -= MOD;\n        return *this;\n    }\n    mint &operator*=(const mint\
    \ &p) {\n        n = 1ll * n * p.n % MOD;\n        return *this;\n    }\n    mint\
    \ &operator/=(const mint &p) {\n        *this *= p.inverse();\n        return\
    \ *this;\n    }\n    mint operator-() const { return mint(-n); }\n    mint operator+(const\
    \ mint &p) const { return mint(*this) += p; }\n    mint operator-(const mint &p)\
    \ const { return mint(*this) -= p; }\n    mint operator*(const mint &p) const\
    \ { return mint(*this) *= p; }\n    mint operator/(const mint &p) const { return\
    \ mint(*this) /= p; }\n    bool operator==(const mint &p) const { return n ==\
    \ p.n; }\n    bool operator!=(const mint &p) const { return n != p.n; }\n\n  \
    \  friend ostream &operator<<(ostream &os, const mint &p) {\n        return os\
    \ << p.n;\n    }\n    friend istream &operator>>(istream &is, mint &p) {\n   \
    \     int x;\n        is >> x;\n        p = mint(x);\n        return is;\n   \
    \ }\n    mint pow(int64_t x) const {\n        mint res(1), mul(n);\n        while\
    \ (x > 0) {\n            if (x & 1) res *= mul;\n            mul *= mul;\n   \
    \         x >>= 1;\n        }\n        return res;\n    }\n    mint inverse()\
    \ const {\n        return mint(modinv(n,MOD));\n    }\n};\n/*\n@brief mod int\n\
    @docs docs/modint.md\n*/\n#line 3 \"math/Combination.cpp\"\n\ntemplate <int MOD>\n\
    struct Combination {\n    using modint = mint<MOD>;\n    vector<modint> perm,\
    \ inv;\n\n    Combination(int x = 1e6) {\n        perm.resize(x);\n        inv.resize(x);\n\
    \        perm[0] = modint(1);\n        REP(i, x + 1)\n        perm[i] = perm[i\
    \ - 1] * i;\n        inv[x] = perm[x].pow(MOD - 2);\n        for (int i = x -\
    \ 1; i >= 0; i--) {\n            inv[i] = inv[i + 1] * (i + 1);\n        }\n \
    \   }\n    modint nCk(int x, int y) {\n        if (x < y) return modint(0);\n\
    \        return perm[x] * inv[x - y] * inv[y];\n    }\n};\n/*\n@brief Combination\
    \ (nCk)\n@docs docs/Combination.md\n*/\n#line 4 \"test/Combination.test.cpp\"\n\
    \nint main(){\n\tcin.tie(0);ios::sync_with_stdio(false);\n\tconst int mod=1e9+7;\n\
    \tCombination<mod>C;\n\tint n,k;cin>>n>>k;\n\tcout<<C.nCk(k,n)<<\"\\n\";\n}\n"
  code: "#define PROBLEM \"https://onlinejudge.u-aizu.ac.jp/courses/library/7/DPL/5/DPL_5_E\"\
    \n\n#include \"math/Combination.cpp\"\n\nint main(){\n\tcin.tie(0);ios::sync_with_stdio(false);\n\
    \tconst int mod=1e9+7;\n\tCombination<mod>C;\n\tint n,k;cin>>n>>k;\n\tcout<<C.nCk(k,n)<<\"\
    \\n\";\n}"
  dependsOn:
  - math/Combination.cpp
  - math/modint.cpp
  - template/template.cpp
  - math/extgcd.cpp
  isVerificationFile: true
  path: test/Combination.test.cpp
  requiredBy: []
  timestamp: '2020-12-20 09:59:48+09:00'
  verificationStatus: TEST_ACCEPTED
  verifiedWith: []
documentation_of: test/Combination.test.cpp
layout: document
redirect_from:
- /verify/test/Combination.test.cpp
- /verify/test/Combination.test.cpp.html
title: test/Combination.test.cpp
---