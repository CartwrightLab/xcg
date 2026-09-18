# XCG: Expanded Congruential Generator

XCG is a family of random number generators inspired by and derived from PCG's
extended generation scheme <https://www.pcg-random.org/>. At its core, XCG is a
128-bit linear congruential generator that returns its high 64-bits. This
simple generator is enough to pass PractRand tests (other than TMFn which is
designed to detect LCGs.) For flexibility, the family provides generators that
vary in the sizes of their parameter spaces. For example, XCG-1280 has 1280
bits of parameter-space: 128 bits for the state of the LCG, 128 bits for the
increment of the LCG, and 1024 bits for a set of 64-bit salts that are mixed
into the output.

## Period

The period of XCG is 2^126 if using the MCG core generator or 2^128 if using
the LCG core generator. While the increment and salts expand the size of XCG's
parameter space, they do not extend XCG's period. The periods of the core
generators are big enough that no application will ever wrap around during
normal usage. This simplifies XCG's algorithm without sacrificing utility or
parameter-space flexibility.
