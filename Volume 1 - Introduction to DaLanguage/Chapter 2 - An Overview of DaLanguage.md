# An Overview of DaLanguage

DaLanguage is organized into 3 layers:

1. The instruction layer;
2. The trait layer;
3. The meta layer.

They're called layers since they layer on top of one another. Any program in the
instruction layer is a valid program in both the trait layer and meta layer.
Conversely, any valid program in the trait layer is a valid program in the meta
layer.

The 3 layers can be seen as supersets of each other, the trait layer adds
features to the instruction layer, and the meta layer adds features to the trait
layer.

The relation between them is analogous to that of the C programming language and
the C preprocessor.

## Why layers?

DaLanguage is made in a layered fashion to manage complexity. By separating
them, DaLanguage tools are easier to create, since each layer is made so that it
can be reduced to the previous. A small number of complex programs can reduce
the meta and trait layer down to the instruction layer, since the top two layers
are far more complex than the bottom layer. On the other hand, a large number
of simple programs can then consume the instruction layer to produce output in a
variety of formats, since the instruction layer is made to be as simple as
possible, while still being a good foundation for DaLanguage.

From a pedagogical perspective, it is far easier to learn each layer one by one,
as each builds on the previous. This volume is structured around that, and the
next part will focus on exploring the instruction layer, then the trait layer
and finally the meta layer.

From a practical viewpoint, the layers are of no concern. There isn't a
practical reason to restrict usage of layers, save for bootstrapping. You should
always use DaLanguage's full feature set.

## What each layer does

Roughly each layer has the following responsibilities:

1. The instruction layer -- a solid, minimal and simple foundation on which
   DaLanguage is founded. It defines instructions, the building blocks of each
   DaLanguage program, how they work, and how they're manipulated;
2. The trait layer -- describes and validates DaLanguage program's semantics. It
   is the "dynamic semantics" part of DaLanguage. It continues where the
   instruction layer leaves, adding fully specified semantics to each
   instruction, along with validation and model checking. Basically a full-blown
   SMT solver;
3. The meta layer -- allows for the addition of new syntax to each DaLanguage
   program. It is the "dynamic syntax" part. It allows for new shorthands to be
   defined, new constructs, and just about any patter that can be mapped to the
   trait layer. It is essentially a parser generator that requires parsing be
   mappable to the previous layer.

## File extensions

DaLanguage program files need to have the `.dal` extension, short for
**DaL**anguage.

If a program intentionally limits its usage of DaLanguage to one layer, then
its file needs to have the one of the following extensions:

- `.dali` if it is limited to the instruction layer, short for **DaL**anguage
   **i**nstructions;
- `.dalt` if it is limited to the trait layer, short for **DaL**anguage
  **t**raits;
- `.dalm` if it is limited to the meta layer, short for **DaL**angauge **m**eta.

In general, don't overthink it and put `.dal` as the extension.

## Conclusion

Like onions, DaLanguage has layers, and like onions, you eat every layer.
However, you peel onions layer by layer.
