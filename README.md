# SimpleTableGenerator

## About

This library is for drawing text tables.

Pass a 2D-list of strings representing cells and get a single string with table contents.

```
makeDefaultSimpleTable :: [[String]] -> String
```

Newlines are supported.

## Basic usage

```
putStrLn $ makeDefaultSimpleTable [["1","2","3"], ["One","Two","Three"], ["First", "Second"]]
```
```
┌───────┬────────┬───────┐
│ 1     │ 2      │ 3     │
├───────┼────────┼───────┤
│ One   │ Two    │ Three │
├───────┼────────┼───────┤
│ First │ Second │       │
└───────┴────────┴───────┘
```

## Advanced usage

You can configure the table by constructing `SimpleTableConfig` and passing it to `makeSimpleTable`.

```
putStrLn $ makeSimpleTable simpleTableConfig {
    tableBorders = "+++++++++-|",
    colMinWidths  = [3, 4],
    rowMinHeights = [2],
    padFunction   = simpleTableLeftPad,
    cellPadFunction = simpleTableBottomPad,
    horizontalPadding = 0,
    verticalPadding = 1,
    paddingStr = ".,`"
    } [["a"], ["b", "c"]]
```
```
+---+----+
|.,`|.,`.|
|.,a|.,`.|
|.,`|.,`.|
|.,`|.,`.|
+---+----+
|.,`|.,`.|
|.,b|.,`c|
|.,`|.,`.|
+---+----+
```

Check out the docs for more info.