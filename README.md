# gigs

> A jobs/careers/openings/positions aggregator

## Install

```bash
npm install --save gigs
```

## Usage

```js
const gigs = require('gigs');

const foo = require('gigs-adapter-foo-jobs');

gigs([foo])
  .process()
  .then(gigs => {
    console.log(gigs);
    //=> [ {title: 'Senior Node.js Developer'}, ... ]
  });
```

## API

### gigs(adapters)

Returns a new `Processor` instance set up with `adapters`.

A `Processor` has only a `process()` method which runs its adapters and returns
a `promise` with the results.

#### adapters

Type: `array`

An array of adapters.

### gigs.create(data)

Returns a `gigs` object.

Use this method in your adapter to create a `gigs` object.

#### data

Type: `object`

A plain object used to populate the `gigs` object.

## Further notes

### Adapter

An adapter is a `function` that returns an `array` of `gigs` objects wrapped in a `promise`.

It retrieves data, transforms it, and returns it.

Each adapter is an npm module with a name in the format of `gigs-adapter-<adapter-name>`,
e.g. `gigs-adapter-stackoverflow-jobs`.

### Gigs

A `gigs` object is a plain object with these members:

#### source

Type: `string`

Name of the adapter, e.g. `gigs-adapter-stackoverflow-jobs`.

#### source_url

Type: `string`

URL of the site where the data comes from, e.g. `http://awesome-job-board.foo`

#### title

Type: `string`

Name of the position, e.g. `Senior Vice President Jr.`

#### description

Type: `string`

Description of the position, e.g. `We're looking for fearless Taco Chef here at "Only Vegan Food, Inc."`

#### url

Type: `string`

URL where you can find more information about the position, e.g. `http://only-vegan-food.foo/careers/taco-chef`

#### company_name

Type: `string`

Name of the company offering the position, e.g. `Only Vegan Food, Inc.`

#### location

Type: `string`

Location of the position. `null` for remote positions, e.g. `San Francisco, CA, US`

#### term

Type: `string`

`full-time`, `part-time` or `contract`.

#### remote

Type: `boolean`

Whether the position is remote (or allows remote).

#### published_at

Type: `string`

Publication date of the position in `YYYY-MM-DD` format, e.g. `2016-12-16`

## License

MIT © Alejandro Beltrán