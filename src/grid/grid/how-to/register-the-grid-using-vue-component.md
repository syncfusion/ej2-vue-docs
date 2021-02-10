---
title: "Register the Grid using Vue.Component"
component: "Grid"
description: "Learn how to register the Grid using Vue.Component."
---

# Register the Grid using Vue.Component

Import the `GridComponent` from the `@syncfusion/ej2-vue-grids` package,register the same using the `Vue.component()` with name of
the grid selector and the GridComponent as its arguments.

Refer to the code example given below.

```typescript
import { GridComponent } from '@syncfusion/ej2-vue-grids';

Vue.component('ejs-grid', GridComponent);
```

Using `Vue.component` will register the grid component alone. Child directives such as `Columns` and `Aggregates` need to be registered separately.

Refer to the code example given below to register column directives

```typescript
import { ColumnsDirective, ColumnDirective } from '@syncfusion/ej2-vue-grids';

Vue.component('e-columns', ColumnsDirective);
Vue.component('e-column', ColumnDirective);
```

Refer to the code example given below to register aggregates directives

```typescript
import { AggregatesDirective, AggregateDirective, AggregateColumnsDirective, AggregateColumnDirective } from '@syncfusion/ej2-vue-grids';

Vue.component('e-aggregates', AggregatesDirective);
Vue.component('e-aggregate', AggregateDirective);
Vue.component('e-columns', AggregateColumnsDirective);
Vue.component('e-column', AggregateColumnDirective);
```