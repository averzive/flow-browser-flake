# Flow Browser Flake

This is a simple Nix flake for installing [Flow Browser](https://flow-browser.com/), a privacy-focused web browser


> [!NOTE]  
> Currently supports **x86_64-linux** systems only 

## Usage

### 1. Add the Flake to Your Inputs

Add the Flow Browser flake to your `flake.nix`'s inputs:

```nix
# flake.nix
inputs = {
    flow-browser = {
        url = "github:averzive/flow-browser-flake/main";
        inputs.nixpkgs.follows = "nixpkgs";
    };

    # ...
};
```

### 2. Include the Package

You can include the Flow Browser package either via **NixOS system configuration** or **Home Manager**

#### Option 1: NixOS System Configuration
```nix
# configuration.nix
environment.systemPackages = [
    inputs.flow-browser.packages.x86_64-linux.default
];
```

#### Option 2: Home Manager
```nix
# home.nix
home.packages = [
    inputs.flow-browser.packages.x86_64-linux.default
];
```

### 3. Rebuild the configuration

Rebuild the system or user environment to install Flow Browser

### For NixOS:
```bash
$ sudo nixos-rebuild switch --flake path/to/flake#hostname
```

### For Home Manager:
```bash
$ home-manager switch --flake path/to/flake#username
```

### 4. Run Flow Browser

After installation, you can launch Flow Browser from your application menu or by running `flow` in your terminal