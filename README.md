# algorithms-testing

## Javascript testing for different algorithm solutions

### Install
Pre-requisites : Install Node & NPM
```
mkdir algos
cd algos
npm init and accept all defaults
npm install -g mocha
npm install mocha chai --save
```

### Mocha
#### Testing script ShanthiKarunakaran-test.js
```
var should = require( 'chai' ).should();
var basic = require( './multShanthiKarunakaran' );

describe('basic', function() {
  it('should return 23 when passed 10', function() {
    basic(10).should.equal(23);
  })
  it('should return 78 when passed 20', function() {
    basic(20).should.equal(78);
  })
  it('should return 2318 when passed 100', function() {
    basic(100).should.equal(2318);
  })
  it('should return 23331668 when passed 10000', function() {
    basic(10000).should.equal(23331668);
  })
  it('should return 486804150 when passed 45678', function() {
    basic(45678).should.equal(486804150);
  })
})
```
#### The js file to be tested
```
function multShanthiKarunakaran(times) {
 var total = 0;
	while(times > 1) {
    times--;
    if(times % 3 == 0 || times % 5 == 0) {
      total +=times;
    }
  }
  return total;
}

multShanthiKarunakaran(45678);

module.exports = multShanthiKarunakaran;
```
#### Run the testing script using mocha
```
 mocha ShanthiKarunakaran-test.js
```
#### Mocha test results
```
multShanthiKarunakaran
    ✓ should return 23 when passed 10
    ✓ should return 78 when passed 20
    ✓ should return 2318 when passed 100
    ✓ should return 23331668 when passed 10000
    ✓ should return 486804150 when passed 45678


  5 passing (18ms)
```
### Benchmark npm module
#### Use benchmarkjs with Node.js 6.5 to determine efficiency
#### Create a benchmark file multShanthiKarunakaran-benchmark.js
```
var Benchmark = require('benchmark');
var suite = new Benchmark.Suite;
var multShanthiKarunakaran = require('./multShanthiKarunakaran.js');

// add tests
suite
  .add('multShanthiKarunakaran Reduce 10000', () => {
    multShanthiKarunakaran(10000);
  })
  .on('cycle', (event) => {
    console.log(String(event.target));
  })
  .on('complete', function () {
    console.log('   Fastest is ' + this.filter('fastest').map('name'));
    console.log('   done!');
  })
    // run async
  .run({ 'async': true });
```
### 
### Run test
#### Use node ShanthiKarunakaran-benchmark.js
```
multShanthiKarunakaran x 560 ops/sec ±7.60% (38 runs sampled)
```
#### For large number 10000 
```
multX.js:58 multX x 629 ops/sec ±9.86% (41 runs sampled)
```
