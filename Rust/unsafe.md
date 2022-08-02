# **Unsafe**
- By nature, static analysis is conservative, when Rust compiler tries to determine whether or not code upholds the guarantees, it's better for the compiler to reject some valid programs rather than accept some invalid programs
- although the Rust code might looks okay (no problem), if Rust compiler doesnt have enough information to be confident, it will reject these codes
- in these cases, we can use `unsafe` to tell the compiler, `trsut me, I know what I'm doing`. The downside is that we use it at our own risk, and if we use unsafe code incorrectly, problems due to memory unsafety, such as null pointer derefencing can occer