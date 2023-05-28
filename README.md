# Deno example, install, testing

With recent release of Deno v 1.34 it seems to be a good time to look a bit deeper at this project. Deno is written in Rust with security in mind and many useful features. It is not only a runtime for TypeScript and JavaScript applications. It is also a complete tool chain. Apart from being a runtime, the second most common use case is to do testing with Deno.

## Deno Cli tool install

e.g. for Ubuntu:
``` bash
sudo apt update
sudo apt install -y curl unzip
curl -fsSL https://deno.land/x/install/install.sh | sh
```

Works on macOS (x64 and arm64), Linux, and Windows (x64 only).  More information is available in [official documentation](https://deno.com/manual@v1.34.0/getting_started/installation). Unfortunately official Deno builds for Linux aarch64 are not available [see issue #1846](https://github.com/denoland/deno/issues/1846#issuecomment-1551447956), but you can try to build your own (e.g. Ubuntu: `sudo apt install build-essential` then [install rust](https://rustup.rs/) and then `cargo install deno`) or install via unofficial `curl -fsSL https://noxifoxi.github.io/deno_install-arm64/install.sh | sh` ([github noxifoxi](https://github.com/noxifoxi/deno_install-arm64), worked fine on Nvidia Tegra).

## IDE - VS Code Deno plugin

Developers agree VS Code is useful IDE ([install instructions](https://code.visualstudio.com/download)) plus [a deno plugin](https://github.com/denoland/vscode_deno) is available ([deno documentation](https://deno.com/manual@v1.34.0/references/vscode_deno#configuring-the-extension) - need to enable a workspace).

## Typescript example - with NPM package

NPM package support is available in Deno, so it is possible to try something like:
``` typescript
import { plot } from "npm:asciichart";
const s0 = new Array(50);
for (let i = 0; i < s0.length; i++) {
  s0[i] = 8 * Math.sin(i * ((Math.PI * 4) / s0.length));
}
console.log(plot(s0));
```
And by running via `deno run -A deno.sinus.terminal.ts` you get a sinus in the terminal:
```
       7.98 ┤    ╭──╮                     ╭──╮                 
       6.99 ┤   ╭╯  ╰╮                   ╭╯  ╰╮                
       5.99 ┤   │    ╰╮                  │    ╰╮               
       4.99 ┤  ╭╯     ╰╮                ╭╯     ╰╮              
       3.99 ┤ ╭╯       │               ╭╯       │              
       2.99 ┤ │        ╰╮              │        ╰╮             
       2.00 ┤╭╯         │             ╭╯         │             
       1.00 ┤│          ╰╮            │          ╰╮            
       0.00 ┼╯           │           ╭╯           │            
      -1.00 ┤            ╰╮          │            ╰╮           
      -2.00 ┤             │         ╭╯             │         ╭ 
      -2.99 ┤             ╰╮        │              ╰╮        │ 
      -3.99 ┤              │       ╭╯               │       ╭╯ 
      -4.99 ┤              ╰╮     ╭╯                ╰╮     ╭╯  
      -5.99 ┤               ╰╮    │                  ╰╮    │   
      -6.99 ┤                ╰╮  ╭╯                   ╰╮  ╭╯   
      -7.98 ┤                 ╰──╯                     ╰──╯    
```

# Testing with Deno

[testing deno doc](https://deno.com/manual@v1.34.0/basics/testing)

[testing in deno - part 1 of 5](https://medium.com/deno-the-complete-reference/testing-with-deno-part-5-integration-tests-efcac6570b0d)

