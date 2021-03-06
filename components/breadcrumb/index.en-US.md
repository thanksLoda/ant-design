---
category: Components
type: Navigation
title: Breadcrumb
---

A breadcrumb displays the current location within a hierarchy. It allows going back to states higher up in the hierarchy.

## When To Use

- When the system has more than two layers in a hierarchy.
- When you need to inform the user of where they are.
- When the user may need to navigate back to a higher level.
- When the application has multi-layer architecture.

## API

| Property      | Description                              | Type              |  Optional | Default |
|-----------|-----------------------------------|-----------------|---------|--------|
| routes    | The routing stack information of router | Array             |         | -      |
| params    | Routing parameter                        | Object            |         | -      |
| separator | Custom separator                      | String or Element |         | '/'    |
| itemRender | Custom item renderer | (route, params, routes, paths) => React.ReactNode | | - |

> `linkRender` and `nameRender` were removed after `antd@2.0`, please use `itemRender` instead.

### Use with browserHistory

The link of Breadcrumb item contain `#` defaultly, you can use `itemRender` to make `browserHistory` Link.

```jsx
import { Link } from 'react-router';

function itemRender(route, params, routes, paths) {
  const last = routes.indexOf(route) === routes.length - 1;
  return last ? <span>{route.breadcrumbName}</span> : <Link to={paths.join('/')}>{route.breadcrumbName}</Link>;
}

return <Breadcrumb itemRender={itemRender} />;
```
