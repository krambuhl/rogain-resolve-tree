# rogain-resolve-tree

Resolve rogain tree with given data into simple dom tree.  The output dom tree is useful for render to string or diffing sets of trees.

## Example

```js
import tree from './template.json';
import data from './data.json';

const currentTreeState = resolveTree(tree, data, config);
```

## resolveTree(tree, props, options)

Resolves a rogain tree into a simple dom tree with a given set of properies.

___tree___

Object in Rogain tree format.

___props___

Object.

___options___

`options.components` optional `rogain-registry` instance. defines components used in resolution.


### Output

The output of the resolveTree function will be a basic dom tree.

__Input Rogain Template__

```html
<Each data={friends} as="friend">
  <Friend data={friend} />
</Each>
```

__Friend Component__

```html
<h2 class="friend">{@attrs.data.firstName} {@attrs.data.lastName}</h2>
```

__Input Data Object__

```js
{
  friends: [{
    firstName: 'Ben',
    lastName: 'Forester'
  }, {
    firstName: 'Larry',
    lastName: 'Forman'
  }]
}
```

__Output Tree__

```js
[{
  type: 'tag',
  name: 'h2',
  attribs: { class: 'friend' },
  children: ['Ben Forester']
}, {
  type: 'tag',
  name: 'h2',
  attribs: { class: 'friend' },
  children: ['Larry Forman']
}]
```

## Install

With [npm](https://www.npmjs.com) do:

```
npm install rogain-resolve-tree
```

## License

MIT
