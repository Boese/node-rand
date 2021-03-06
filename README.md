![David](https://img.shields.io/david/Boese/node-rand)
![David](https://img.shields.io/david/dev/Boese/node-rand)
![Travis (.com)](https://img.shields.io/travis/com/Boese/node-rand)

<h1>NodeJS native addon wrapper around c++ random library</h1>

Goal is to instead of allocating an array of size n, use the NodeJS Streaming API
to write random numbers to a fixed_size buffer back to javascript. This will hopefully
save some memory, not block eventloop. 

Class should be able to generate reproducible random numbers per instance based on seed.
This will wrap c++ <random> library.
Should be able to create any random number or sequence of type compatible with JS
> Supported JS Types: int8, uint8, int16, uint16, int32, uint32, double, int64 (limit by js MAX NUM), big_int64, big_uint64


<ul>
<li>NOTE: if seed is not set, random one will be used.</li>
</ul>

<h3>Proposed API</h3>

```c++
class RandSeed (implement NodeJS.Writeable stream) {
    public:
        /*Currently implemented*/

        RandSeed();
        void SetSeed(int64_t num) // set seed;

        int64_t Generate(int64_t min, int64_t max) // send a random number immediately

        void GenerateSequenceStream(int64_t min, int64_t max, uint64_t size) // sends random numbers to the underlying stream buffer

        /* Future will support all types. Will be additional enum param to Generate, GenerateSequenceStream */
};
```

<h2>TODO</h2>
<ul>
    <li>Update README with how to use</li>
    <li>Add badge for coverage</li>
    <li>publish to npm</li>
    <li>[FUTURE] Long term goal is to recreate c++ std <random> in addon, supporting both distributions and generators</li>
</ul>



