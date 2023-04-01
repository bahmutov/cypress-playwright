# cypress-playwright
> Run Cypress tests using Playwright and Playwright tests using Cypress

This package provides a bridge between Cypress and Playwright test runners. You can execute Cy tests using Pw and the inverse.

## Install

```
# install this package using NPM
$ npm i -D cypress-playwright
# or using Yarn
$ yarn add -D cypress-playwright
```

If using Cypress, add this package to your [Cypress support file](https://on.cypress.io/support-file)

```js
// cypress/support/e2e.js
import 'cypress-playwright'
```

Voilá you can now run your Playwright tests in Cypress and Cypress tests in Playwright! Plus use `await` keyword with all Cypress commands:

```js
// Cypress spec
await it('works', async () => {
  await cy.visit('/')
  const $el = await cy.get('selector')
  expect($el).to.be.visible
  // or use "should" assertions
  $el.should.be.visible
})
```

Want to open 2nd tab and test your chat application? No problem!

```js
// Cypress spec
cy.get('selector button').click() // opens the second tab
// use PW syntax to wait for the 2nd tab to open
const secondPage = await context.waitForEvent('page')
await newPage.waitForLoadState()
// continue using Cy to test the second page
cy.get('selector on the second tab').type('something')
// now close the 2nd page and switch to the first
cy.get('close button selector').click()
// or simply use
await newPage.close()
// we are back on the first page!
```

## Small print

Author: Gleb Bahmutov &lt;gleb.bahmutov@gmail.com&gt; &copy; 2023

- [@bahmutov](https://twitter.com/bahmutov)
- [glebbahmutov.com](https://glebbahmutov.com)
- [blog](https://glebbahmutov.com/blog)
- [videos](https://www.youtube.com/glebbahmutov)
- [presentations](https://slides.com/bahmutov)
- [cypress.tips](https://cypress.tips)
- [Cypress Tips & Tricks Newsletter](https://cypresstips.substack.com/)
- [my Cypress courses](https://cypress.tips/courses)

License: MIT - do anything with the code, but don't blame me if it does not work.

Support: if you find any problems with this module, email / tweet /
[open issue](https://github.com/bahmutov/cypress-playwright/issues) on Github

## MIT License

Copyright (c) 2023 Gleb Bahmutov &lt;gleb.bahmutov@gmail.com&gt;

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

April 1st 2023
