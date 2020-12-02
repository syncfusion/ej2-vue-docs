---
title: "Feature Modules"
component: "Grid"
description: "Learn what are the feature Modules available and how to use it in DataGrid."
---

# Feature Modules

The following modules should be injected to extend grid's functionality.

The available grid modules are

| Module | Description |
|------|-------------|
| [`Page`](../api/grid/page/)| Inject this module to use paging feature.|
| [`Sort`](../api/grid/sort/)| Inject this module to use sorting feature.|
| [`Filter`](../api/grid/filter/)| Inject this module to use filtering feature.|
| [`Group`](../api/grid/group/)| Inject this module to use grouping feature|
| [`Edit`](../api/grid/edit/)| Inject this module is use editing feature.|
| `Aggregate`| Inject this module to use aggregate feature.|
| [`ColumnChooser`](../api/grid/columnChooser/)| Inject this module to use column chooser feature.|
| `ColumnMenu`| Inject this module to use column menu feature.|
| `CommandColumn`| Inject this module to use command column feature.|
| [`ContextMenu`](../api/grid/contextMenu/)| Inject this module to use context menu feature.|
| [`DetailRow`](../api/grid/detailRow/)| Inject this module to use detail template feature.|
| `ForeignKey`| Inject this module to use foreign key feature.|
| `Freeze`| Inject this module to use frozen rows and columns feature.|
| `Resize`| Inject this module to use resize feature.|
| [`Reorder`](../api/grid/reorder/)| Inject this module to use reorder feature.|
| `RowDD`| Inject this module to use row drag and drop feature.|
| [`Search`](../api/grid/search/)| Inject this module to use search feature and this is a default injected module.|
| [`Selection`](../api/grid/selection/)| Inject this module to use selection feature and this is a default injected module.|
| [`Scroll`](../api/grid/scroll/)| Inject this module to use scrolling feature and this is a default injected module.|
| [`Print`](../api/grid/print/)| Inject this module to use to use print feature and this is a default injected module.|
| `Toolbar`| Inject this module to use toolbar feature.|
| `VirtualScroll`| Inject this module to use virtual scroll feature.|
| `ExcelExport`| Inject this module to use excel export feature.|
| `PdfExport`| Inject this module to use PDF export feature.|

These modules should be injected into the `provide` section and use `grid` as a key of the object.
