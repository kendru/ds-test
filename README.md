# ds-tpl

Dead-simple, fast text templates.

Mustache-style templates that perform only interpolation and iteration.
No logic, no filtering, no extra features.

Is it fast? Yes.

### Usage

```javascript
const compileTemplate = require('ds-tpl');

// Example 1: Simple interpolation
const tpl = compileTemplate('Hello, {{world}}');
const data = { world: 'Earth' };

console.log(tpl(data)); // Logs: "Hello, Earth"

// Example 2: Iteration and property access
const tpl = compileTemplate(
`The first planet's name is: {{planets.0.name}}. All of them are:{% for planets as planet %}
    - {{planet.name}}{% endfor %}`
);
const planets = [
    { name: 'Mercury' },
    { name: 'Venus' },
    { name: 'Earth' },
    { name: 'Mars' },
    { name: 'Jupiter' },
    { name: 'Saturn' },
    { name: 'Uranus' },
    { name: 'Neptune' }
];

console.log(tpl({ planets }));
/* Logs:
 * The first planet's name is: Mercury. All of them are:
 *  - Mercury
 *  - Venus
 *  - Earth
 *  - Mars
 *  - Jupiter
 *  - Saturn
 *  - Uranus
 *  - Neptune
 */
```
