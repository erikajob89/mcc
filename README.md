# mcc
Another MicroC compiler. This essentially a fork of the reference compiler for Columbia's _Programming Languages and Translators_ course. The original can be found at https://github.com/cwabbott0/microc-llvm. Students in the class are allowed to write the compiler for their own final semester project in OCaml or Haskell, but since the provided reference compiler is in OCaml, almost no one chooses Haskell. This project is an attempt to remedy that situation and open the possibility of using Haskell to more students.

## Setup
`mcc` requires the `stack` package manager for Haskell. To install `stack`, see https://docs.haskellstack.org/en/stable/README/. It also requires that `clang` and `llc` binaries be available in your PATH. There are two options to ensure that these will be available:
1. **Use Nix**:
Using `stack`'s `nix` integration will set up a local environment with the correct versions of `clang` and `llc` installed and added to the PATH. To acquire nix, follow the installation [instructions](https://nixos.org/nix/download.html). Then, simply append a `--nix` flag to all `stack` commands and everything should "just work." If not, please raise an issue.
2. **Manual Installation**:
To install the `llvm` toolchain, which includes `llc`, `clang`, and a host of other compiler tools, go to http://releases.llvm.org/download.html#6.0.1. For macOS, the maintainers of the Haskell-LLVM bindings provide a brew tap, so running `brew install llvm-hs/llvm/llvm-6.0` and adding `/usr/local/opt/llvm/bin` to your `$PATH` should be sufficient. They also provide more [detailed instructions](https://github.com/llvm-hs/llvm-hs#installing-llvm) on how to install llvm on other platforms. Note that unlike the OCaml version of MicroC, this project requires LLVM 6, not LLVM 3.4. 

## Running and testing the compiler
Once everything is installed, to run the compiler's test suite, navigate to the project home directory and run `stack test`. To build compiler executable, run `stack build mcc`. Remember to add `--nix` to these commands if you would like `nix` integration. If you would like integration by default, change `enable: false` to `enable: true` in `stack.yaml` under the nix section.

## Questions, contributions
Please don't hesitate to open an issue or pull request if you don't understand something in here or you see something that could be improved! Once most of the functionality is complete, I'm planning on releasing a detailed walkthrough on the whole compilation process in a series of posts, but until then, documentation is very sparse.
