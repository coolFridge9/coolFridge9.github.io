---
layout: post
title: Testing in Javascript
---

* 'describe' is used to describe a group of tests
* 'it' is used to describe an individual test

```javascript

describe("System Instance Healthcheck Controller", () => {
    describe("get() action", () => {
        it("should succeed when queried with basic parameters", () => {
            expect(1).toBe(1);
            expect( {x : 1} ).toEqual( {x : 1} );
            expect(x).toBeDefined();
        });
    });
});

```

#### repeditive testing

```javascript
describe.each`
dateNum      | expected                  | testReason
${2141}      | ${new Date(2004, 2, 29)}  | ${"29/2/2004"}
${4189}      | ${new Date(2008, 2, 29)}  | ${"29/2/2008"}
${3677}      | ${null}                   | ${"29/4/2007"}
`("testing leap years", ({dateNum, expected, testReason}) => {
    it(testReason, () => {
        expect(calculateDate(dateNum)).toEqual(expected);
    });
});
```
