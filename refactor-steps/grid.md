
# Refactor - Grid

````md magic-move

```ts
class Position {
  private x = 0
  private y = 0

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    this.wrapAroundGrid()
  }

  private wrapAroundGrid() {
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0
  private xGridSize = 10
  private yGridSize = 10

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    this.wrapAroundGrid()
  }

  private wrapAroundGrid() {
    this.x = (this.x + 10) % 10
    this.y = (this.y + 10) % 10
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0
  private xGridSize = 10
  private yGridSize = 10

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    this.wrapAroundGrid()
  }

  private wrapAroundGrid() {
    this.x = (this.x + this.xGridSize) % this.xGridSize
    this.y = (this.y + this.yGridSize) % this.yGridSize
  }
}
```

```ts
class Position {
  private x = 0
  private y = 0
  private grid = new Grid()

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    this.wrapAroundGrid()
  }

  private wrapAroundGrid() {
    this.x = (this.x + this.xGridSize) % this.xGridSize
    this.y = (this.y + this.yGridSize) % this.yGridSize
  }
}
```

```ts
class Grid {
  private x = 10
  private y = 10
}

class Position {
  private x = 0
  private y = 0
  private grid = new Grid()

  public move({ x, y }: { x: number, y: number }) {
    this.x += x
    this.y += y
    this.wrapAroundGrid()
  }

  private wrapAroundGrid() {
    this.x = (this.x + this.xGridSize) % this.xGridSize
    this.y = (this.y + this.yGridSize) % this.yGridSize
  }
}
```

```ts
class Grid {
  private x = 10
  private y = 10
}

class Position {
  private x = 0
  private y = 0
  private grid = new Grid()

  private wrapAroundGrid() {
    this.x = (this.x + this.xGridSize) % this.xGridSize
    this.y = (this.y + this.yGridSize) % this.yGridSize
  }
}
```

```ts
class Grid {
  private x = 10
  private y = 10

  public get xSize() {
    return this.x
  }

  public get ySize() {
    return this.y
  }
}

class Position {
  private x = 0
  private y = 0
  private grid = new Grid()

  private wrapAroundGrid() {
    this.x = (this.x + this.xGridSize) % this.xGridSize
    this.y = (this.y + this.yGridSize) % this.yGridSize
  }
}
```

```ts
class Grid {
  private x = 10
  private y = 10

  public get xSize() {
    return this.x
  }

  public get ySize() {
    return this.y
  }
}

class Position {
  private x = 0
  private y = 0
  private grid = new Grid()

  private wrapAroundGrid() {
    this.x = (this.x + this.grid.xSize) % this.grid.xSize
    this.y = (this.y + this.grid.ySize) % this.grid.ySize
  }
}
```

````