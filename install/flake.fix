{
 description = "Base system for raspberry pi 4";
 inputs = {
   nixpkgs.url = "nixpkgs/nixos-23.11";
   nixos-generators = {
     url = "github:nix-community/nixos-generators";
     inputs.nixpkgs.follows = "nixpkgs";
   };
 };

 outputs = { self, nixpkgs, nixos-generators, ... }:
 {
   nixosModules = {
     system = {
       disabledModules = [
         "profiles/base.nix"
       ];
       system.stateVersion = "23.11";
     };
     users = {
       users.users = {
         installer = {
           password = "oneT!meW0nder";
           isNormalUser = true;
           extraGroups = [ "wheel" ];
         };
       };
     };
   };

   packages.aarch64-linux = {
     sdcard = nixos-generators.nixosGenerate {
       system = "aarch64-linux";
       format = "sd-aarch64";
       modules = [
         ({ pkgs, ... }: {
           networking.firewall.enable = false;
           nixpkgs.config.allowUnfree = true;
           environment.systemPackages = with pkgs; [ openssh ];
           services.openssh.enable = true;
         })
         self.nixosModules.system
         self.nixosModules.users
       ];
     };
   };
 };
}