# SHA-1 \(Secure Hash 1\)

A cryptographic hash function that produces a 160-bit integer hash from any sequence of bytes. Cryptographic hash functions have the property that it is extremely difficult to find two different byte streams with the same hash value \(or indeed to find _any_ byte stream given just its hash value\), so that essentially, we may assume that the probability that any two objects with different contents have the same SHA-1 hash value is 2-160 or about 10-48. Basically, we simply ignore the possibility of a hashing collision, so that the system has, in principle, a fundamental bug that in practice never occurs!

Most known for its use in Git's commit/object hashing.

Generally implemented in a content-addressable manner, meaning that the generated hashes \(ids\) are _universal_: unlike a typical Java implementation, two objects with exactly the same content will have the same id on all systems \(i.e. my computer, your computer, and anyone else’s computer will compute this same exact id\). In the case of blobs, “same content” means the same file contents.

