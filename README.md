RowSorter.js
============
## Drag 'n drop row sorter plugin.
* Small size - 2kb minified (~8kb non-minified).
* Touch devices are supported.
* Supports IE8+ (not tested with ie7) and all other modern browsers.

### Install
    bower install rowsorter
### Manuel Install
```html
<script type="text/javascript" src="/path/jquery.rowsorter.min.js"></script>
```

### Options:

    handler          : drag handler selector (default: "tr")
    tableDragClass   : adds this class name to table while rows are sorting (default: "sorting-table")
    disabledRowClass : undraggable rows' class name for disabling the drag (default: "nodrag").
    dragClass        : dragging row's class name (default: "sorting-row").
    onDragStart      : (default: null)
    onBeforeMove     : Called before dragged row changes position. Abort move by returning false. (default: null)
    onDrop           : (default: null)

#### Using Event Handlers
```javascript
    onDragStart: function(tbody, row, old_index) {
        // finding the table
        var table = tbody.nodeName === "TBODY" ? tbody.parentNode : tbody;

        // old_index is zero-based index of row in table (or tbody if exists)
        console.log(table, row, old_index);
    }

    onBeforeMove: function(tbody, row, new_index, old_index) {
        // Don't move if the dragged row is about to move to the top.
        // This makes the top row sticky if it's also disabled.
        if (new_index === 0) {
            // Returning false will abort the move.
            return false;
        }
    }

    // if new_index === old_index, this function won't be called.
    onDrop: function(tbody, row, new_index, old_index) {
        // finding the table
        var table = tbody.nodeName === "TBODY" ? tbody.parentNode : tbody;

        // old_index is stored index of row in table/tbody before we have dragged the row.
        // new_index is index of row in table/tbody after the row has been dragged.
        console.log(table, row, new_index, old_index);
    }
```

### Sample Usages

* [Basic Usage][basic]
* [Custom Handler 1][handler1]
* [Custom Handler 2][handler2]
* [Move Handler][movehandler]
* [Disabled Row][disabled]
* [Custom CSS][style]


[basic]: http://borayazilim.com/projects/rowsorter/samples/basic.html
[handler1]: http://borayazilim.com/projects/rowsorter/samples/handler1.html
[handler2]: http://borayazilim.com/projects/rowsorter/samples/handler2.html
[movehandler]: http://borayazilim.com/projects/rowsorter/samples/move-handler.html
[disabled]: http://borayazilim.com/projects/rowsorter/samples/disabled.html
[style]: http://borayazilim.com/projects/rowsorter/samples/style.html
