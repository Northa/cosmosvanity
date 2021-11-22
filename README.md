# Umee_vanity

<!--- Don't edit the version line below manually. Let bump2version do it for you. -->
> Version 1.0.0

> CLI tool for generating [Umee](https://umee.cc/) vanity addresses


<details>
  <summary>Features:</summary>
  
* Generate Umee bech32 vanity addresses
* Use all CPU cores
* Specify a substring that the addresses must
    * start with
    * end with
    * contain
* Set required minimum amount of letters (a-z) or digits (0-9) in the addresses
* Binaries built for Linux, macOS and Windows
  
</details>


<details>
  <summary>Installing:</summary>
  
Download the latest binary release from the [_Releases_](https://github.com/Northa/cosmosvanity/releases) page. 
Alternatively, build from source yourself.

```sh
$ go version
go version go1.17 linux/amd64
$ git clone https://github.com/Northa/cosmosvanity.git && cd cosmosvanity
$ go build -o umee_vanity ./main.go
go: downloading github.com/tendermint/tendermint v0.34.8
go: downloading github.com/cosmos/cosmos-sdk v0.40.0
go: downloading github.com/btcsuite/btcd v0.21.0-beta
go: downloading golang.org/x/crypto v0.0.0-20201221181555-eec23a3978ad

$ sha256sum ./umee_vanity
4ed4758abbbb1f3d4283a95ca18025eb99c73e9fedbf3921b555c27435206a5a  ./umee_vanity
```
  
</details>

## Usage examples
Find an address that starts with "drew" (e.g. umee1drewfmzk3a90m2ldkhxq0q7haaewkvfges05h0)
```sh
./umee_vanity --startswith drew
:::: Matching wallet 1/1 found ::::
Address:        umee1drewfmzk3a90m2ldkhxq0q7haaewkvfges05h0
Public key:     03e6334056ded1918964985d3501f2353a873a1d6c248849fa3c521f7b38a65c96
Private key:    9482108ab9d71fe7cf8c44c52ce2ea869337cb7a362a4d1cc51346b504054ce1
```

Find an address that starts with "nguru" (e.g. umee1ngurugw0m8ultdyr5zqr64puddxd8k5pm6pd80)
```sh
./umee_vanity --startswith nguru
:::: Matching wallet 1/1 found ::::
Address:        umee1ngurugw0m8ultdyr5zqr64puddxd8k5pm6pd80
Public key:     03104814aa00a270f20da6ba5d8ae8172b6d4d5954779c180487997a9558041f8c
Private key:    a79a2db65a5b92bff47bd11253fe880cf0995919bd5e1ab5ce701a909c6af1b1
```

Find an address that ends with "8888" (e.g. umee134dck5uddzjure8pyprmmqat96k3jlypn28888)
```bash
./umee_vanity --endswith 8888
```

Find an address containing the substring "gener" (e.g. umee1z39wgener7azgh22s5a3pyswtnjkx2w0hvn3rv)
```bash
./umee_vanity --contains gener
```

Find an address consisting of letters only (e.g. umee1rfqkejeaxlxwtjxucnrathlzgnvgcgldzmuxxe)
```bash
./umee_vanity --letters 38
```

Find an address with at least 26 digits (e.g. umee1r573c4086585u084926726x535y3k2ktxpr88l)
```bash
./umee_vanity --digits 26
```

Generate 5 addresses (the default is 1)
```bash
./umee_vanity -n 5
```

Restrict to using only 1 CPU thread. This value defaults to the number of CPUs available.
```bash
./umee_vanity --cpus 1
```

Combine flags introduced above
```bash
./umee_vanity --contains 8888 --startswith a --endswith c
```
