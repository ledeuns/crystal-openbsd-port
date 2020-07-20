# Crystal-lang for OpenBSD

Creates a package that installs [Crystal](https://crystal-lang.org/) and
its dependency manager [Shards](https://github.com/crystal-lang/shards)

## Build notes

Since Crystal is self-hosting this port relies on a precompiled object file
which is used to link a bootstrap compiler which is used to compile Crystal.

Remove L88+ to remove usage of OpenSSL v1.1.1 functions in src/openssl/bio.cr
Comment L36 to remove call to LLVMExtTargetMachineEnableGlobalIsel() in src/llvm/target_machine.cr

```
bin/crystal build --cross-compile --target amd64-unknown-openbsdX.X src/compiler/crystal.cr -D i_know_what_im_doing
```

