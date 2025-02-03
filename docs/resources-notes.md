# Resource Manager Notes

## Concepts from the book

The book explains we can split up resource management into:

- Offline resource management and the toolchain

- Runtime resource management

- The toolchain is also called the asset/resource conditioning pipeline

The term asset conditioning pipeline is useful and I'll use it below.

## How are we getting our glTF files?

There is a question of how we are getting our glTF files.

There will be some premade glTF assets we can use but we will have to think about how do we create our own for the game.

We don't have to have a fully fledged toolchain that allows for any asset created by artists to be converted to glTF but we will need some preset models to make obbys with.

## Augmenting glTF? / auxilliary data?

One question to think about, maybe decently early, is the limitations of glTFs and what info they can store. They are quite comprehensive, but if we have a scene editor and want to create an obby with moving platforms, say the platform moves from point A to point B, how do we save out a scene representation and info about this moving platform?

## Packing the TBN frame

One obvious case for where we are going to have to have some sort of asset conditioning pipeline is for packing the TBN frame.

The solution is:

- glTFs store normals

- We are free to store whatever data inside these normals we like

- Take a normal glTF file which holds normals and tangents, calculate the TBN frame

- Output a new glTF file, storing the packed TBN frame into the normals, and get rid of the explicit tangents

How will we implement this though?
